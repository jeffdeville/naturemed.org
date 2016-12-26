# Wordpress Tech

## Common Tasks
* Push database changes from local up
* 
* Pull database changes from production down
* 
* Updating Wordpress
    1. Update as desired: /site/composer.json
    2. Run the following
```
cd ansible && vagrant up
vagrant ssh
cd /srv/www/dev.naturemed.org/current
composer update
```

* Updating Avada stuff
This, I just have to do withing the UI, because I have to have their validation code to do the updates. So:
    1. `cd ansible && vagrant up`
    2. http://naturemed.dev
    3. login
    4. Themes -> Update
    5. Now Avada -> Plugins, and update whatever is needed

* Deploy To Prod
*Note:* This is using my default ssh key, and it needs to be able to pass its creds along as needed, so ssh-add is important
```
cd ansible
# Deploy to dev.naturemed.org
./deploy.sh staging dev.naturemed.org   

# Deploy to www.naturemed.org
./deploy.sh production dev.naturemed.org    
```
---
# Trellis
Virtual machine - php7, nginx
# Bedrock
Use composer to version all of your dependencies.

# WPSync - Database Sync

## Password Issues

My use of wpsync is making it so that all of my passwords are getting pulled from the old site. So if you're wondering why they aren't matching up to what's in the vault, that's why.   

To Fix:
Just create 1 secrets file for dev, staging, and prod, and encrypt them all. Then push that on top of what is on the current systems. this will remove the password from the old dev1, and I can get rid of it.

You're deploying with -e ENV=staging right now!

Next up is going to be to figure out how to use the child theme to update things.
