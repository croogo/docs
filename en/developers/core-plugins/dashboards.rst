Dashboards
##########

Registering Dashboard block
===========================

This is done in ``<Plugin>/Config/admin_dashboard.php``.  It's a typical cakephp config file.  The array key is the dashboard identifier and the value contains the dashboard block setting. It accepts 3 options:
  - title
  - element
    Path to element file containing the Dashboard html code
  - column
    Valid values: ``CroogoDashboard::LEFT``, ``CroogoDashboard::RIGHT``, ``CroogoDashboard::FULL``

Once that is registered, the block should be rendered in the dashboard page.

Displaying Dashboard block contents
===================================

The registered element simply formats and displays data in the page. For
example, the element in Example plugin only has static content.

The built in Dashboards plugin displays Croogo Blog's newsfeed. The Javascript
code in the element retrieves content from https://blog.croogo.org/promoted.rss,
parses the XML and display the blog title as a list of links.

Example: Display list of latest comment messages
------------------------------------------------

Register an Dashboard block in your plugin's admin_dashboard.ctp::

    // Plugin/YourPlugin/Config/admin_dashboard.php
    $config = array(
        'dashboard.latest_comment' => array(
            'title' => 'Latest Comment',
            'element' => 'YourPlugin.dashboards/latest_comments',
            'column' => CroogoDashboard::LEFT,
        ),
    );

The following is an excerpt from the element that renders the dashboard block::

    // Plugin/YourPlugin/View/Elements/dashboard/latest_comments.ctp
    $latestComments = isset($latestComments) ? $latestComments : array();
    foreach ($latestCmments as $comment):
        echo $this->Html->para(null, $comment['Comment']['title']);
    endforeach;

`$latestComments` need to be populated somewhere else. One alternative is to
write a custom component and hook it to the `DashboardsController`::

    // Plugin/YourPlugin/Config/bootstrap.php
    Croogo::hookComponent('Dashboards.Dashboards', 'YourPlugin.LatestComments');

The LatestCommentsComponent simply retrieves the data and send it to view::

    // Plugin/YourPlugin/Controller/Component/LatestCommentsComponent.php
    class LatestCommentsComponent extends Component {

        public startup(Controller $controller) {
            $Comment = ClassRegistry::init('Comments.Comment');
            $latestComments = $Comment->find('all', array(
                'order' => 'created desc',
                'limit' => 10,
            ));
            $controller->set(compact('latestComments'));
        }
    }

