# Mongo db troubleshooting

The problem is described in: 
https://stackoverflow.com/questions/44033079/property-firebase-does-not-exist-on-type-production-boolean


``` js
export const environment = {
  production: true,
  firebase: {
    apiKey: '...',
    authDomain: 'project.firebaseapp.com',
    databaseURL: 'https://project.firebaseio.com',
    projectId: 'project',
    storageBucket: 'project.appspot.com',
    messagingSenderId: '...',
  },
};

```

https://stackoverflow.com/questions/68939014/angularfiremodule-and-angularfiredatabasemodule-not-being-found-in-angular-fire
```

import { AngularFireModule} from '@angular/fire/compat'
import { AngularFireDatabaseModule } from '@angular/fire/compat/database';

//mongo 
```
https://stackoverflow.com/questions/23943651/mongodb-admin-user-not-authorized
```

use admin
db.createUser(
  {
    user: 'user',
    pwd: 'password',
    roles: [ { role: 'root', db: 'admin' }, { role: 'userAdminAnyDatabase', db: 'admin' } ]
  }
);
exit;

db.grantRolesToUser('admin', [{ role: 'root', db: 'admin' }])
db.grantRolesToUser('user', [{ role: 'root', db: 'admin' }])
db.grantRolesToUser('user', [{ role: 'userAdminAnyDatabase', db: 'admin' }])
db.grantRolesToUser('user', [{ role: 'root', db: 'guestbook' }]);
db.grantRolesToUser('user', [{ role: 'userAdminAnyDatabase', db: 'guestbook' }]);



sh-4.2$ mongo -u user -p password --authenticationDatabase admin
MongoDB shell version v3.6.3
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.6.3
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
        http://docs.mongodb.org/
Questions? Try the support group
        http://groups.google.com/group/mongodb-user
Server has startup warnings: 
2023-08-28T14:32:03.454+0000 I STORAGE  [initandlisten] 
2023-08-28T14:32:03.454+0000 I STORAGE  [initandlisten] ** WARNING: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine
2023-08-28T14:32:03.454+0000 I STORAGE  [initandlisten] **          See http://dochub.mongodb.org/core/prodnotes-filesystem
2023-08-28T14:32:04.351+0000 I CONTROL  [initandlisten] 
2023-08-28T14:32:04.351+0000 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2023-08-28T14:32:04.351+0000 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2023-08-28T14:32:04.351+0000 I CONTROL  [initandlisten] 
> 
> show dbs;
admin             0.000GB
config            0.000GB
guestbook         0.000GB
local             0.000GB
meal-tracker-fsa  0.000GB
> 



//

mongoimport -u user -p password --authenticationDatabase admin --db="meal-tracker" --collection="recipes" --file=recipes.json --jsonArray
```

