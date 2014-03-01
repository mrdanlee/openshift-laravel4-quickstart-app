## Openshift Laravel Quickstart
This is an Openshift Quickstart for Laravel 4. It has been configured to utilize your Openshift Origin installation. To provide Laravel 4 as an instant app for Openshift Origin, you will need to modify `/etc/openshift/quickstarts.json` and add the following to the end of the file
```json
{
	"quickstart": {
		"id": "10",
		"name": "Laravel 4",
		"website": "http://www.laravel.com",
		"initial_git_url": "git://github.com/muffycompo/openshift-laravel4-quickstart-app.git",
		"cartridges": ["php-5.4", "mysql-5.5"],
		"summary": "Laravel is a PHP web application framework with expressive, elegant syntax.",
		"tags": ["php", "instant_app", "framework", "mysql"],
		"admin_tags": []
	}
}
```
### Cartridge Requirement
You will need to install the PHP5.4 and MySQL5.5 cartridges before installing this quickstart for Laravel.

####NOTE
You should remove the comment # in `.openshift/actions_hooks/build` by changing
```shell
#( unset GIT_DIR ; cd $OPENSHIFT_REPO_DIR ; php $OPENSHIFT_DATA_DIR/composer.phar -q --no-ansi install )
```
to become
```shell
( unset GIT_DIR ; cd $OPENSHIFT_REPO_DIR ; php $OPENSHIFT_DATA_DIR/composer.phar -q --no-ansi install )
```
Now using git
```shell
git add .
git commit -a -m 'Install Laravel 4 Composer Dependencies'
git push
```
### Post Installation
After the installation of composer dependencies, Laravel is ready to go. We have setup your database credentials `app/config/database.php` to use Openshift environment variables (OPENSHIFT*).