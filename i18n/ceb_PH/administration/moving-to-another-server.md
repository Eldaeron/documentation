# Pagbalhin sa EspoCRM ngadto sa laing serber

Sunda kini nga mga lakang aron mabalhin ang EspoCRM ngadto sa laing serber:

### Una nga lakang. Mga backup file

Pag-abli ug usa ka file manager o pag-login gamit ang SSH para i-archive ang tanang files nga pwede ma-archive gikan sa EspoCRM nga direktoryo: Mga dugang nga detalye: https://github.com/espocrm/documentation/blob/master/administration/backup-and-restore.md#step-1-backup-files.

### Ika-duha nga lakang. Back-upi ang imohang database

Ang data nga nasulod sa database (MySQL, MariaDB) kay gikinahanglan naback-up. Palihug ug sunod sa mga rekomendasyon:
https://github.com/espocrm/documentation/blob/master/administration/backup-and-restore.md#step-2-backup-database.

### Ika-tulo nga lakang. Kopyaha ang mga file ug mga database backup ngadto sa laing serber

Pagkopya og mga backup nga mga file ug ang imohang database ngadto sa bag-ong serber.

### Ika-upat nga lakang. I-unarchive ang mga backup file

Para i-unarchive ang mga backup, pwede kang mugamit og Archive Manager o kani nga mga pagtudlo: https://github.com/espocrm/documentation/blob/master/administration/backup-and-restore.md#step-1-unarchive-backup-files. 
Timan-e: Ang mga file nanginahanglan nga iplastar ngadto sa web-serber nga direktoryo.

### Ika-lima nga lakang. I-konpigyur ang usa ka serber

I-konpigyur ang usa ka bag-ong serber base sa mga rekomendasyon diri: https://www.espocrm.com/documentation/administration/serber-configuration/.

### Ika-unom nga lakang. Sakto nga mga permission

I-set ang mga gikinahanglang mga permission og ang tag-iya sa mga file, https://www.espocrm.com/documentation/administration/serber-configuration/#user-content-required-permissions-for-unix-based-systems.

### Ika-pito nga lakang. I-import ang imohang database backup

Una, gikinahanglan nimong muhimo og bag-o nga database gamit ang usa ka user sa MySQL. Para ma-import ang imohang database gikan sa backup, sunda ang kaning mga giya: https://github.com/espocrm/documentation/blob/master/administration/backup-and-restore.md#step-3-import-database-dump.

### Ika-walo nga lakang. Sakto nga mga EspoCRM configuration

Human sa malampusong pag-import ug pag-konpigyur sa serber, palihug og usab para masakto ang EspoCRM nga mga configuration sa file nga `ESPOCRM_DIRECTORY/data/config.php`:

 * mga setting sa koneksyon sa database:
  
  ```php
  'database' => [
        'driver' => 'pdo_mysql',
        'dbname' => 'PANGALAN_SA_IMONG_DATABASE',
        'user' => 'IMOHANG_USER',
        'password' => 'IMOHANG_DATABASE_PASSWORD',
        'host' => 'localhost',
        'port' => ''
    ],
  ```
   
   * "siteUrl" - kung ang pangalan sa imohang domain (URL) kay nausab:
  
  ```php
  'siteUrl' => 'https://new-link.com',
  ```
  
  * tag-iya sa mga default file (kung lahi ra):
  
  ```php
  'defaultPermissions' => [
        'user' => 'www-data',
        'group' => 'www-data'
    ]
  ```

  kung asa ang `www-data` kay ang web-serber nga user.

### Ika-siyam nga lakang. Pag-setup sa usa ka crontab

Pag-setup sa usa ka crontab, https://www.espocrm.com/documentation/administration/serber-configuration/#user-content-setup-a-crontab.
Timan-e: gikinahanglan i-konpigyur kini gamit ang imohang web-serber nga user.

Mao ra tong tanan. Karon, ang imohang EspoCRM instance kay nagdagan sa bag-o nga serber.
