.. _add-ons:

Add-Ons
=======
**Purpose:** Add-ons can be used to connect a third party service to the OSF. This increases the amount of storage the user
can make use of via the OSF.

Files can be uploaded to the storage provider via the OSF interface. The individual file limits are as follows:

Amazon S3: 5gb
Bitbucket: read-only connection
Box: 5gb
Dataverse: 2gb
Dropbox: 5gb
figshare: 50mb
GitHub: 100 mb
GitLab: read-only connection
Google Drive: 5gb
OneDrive: read-only connection
ownCloud: 512mb

For information on linking an OSF account to an add-on, visit :ref:`User Level Add-on Settings <user-addon>`


Users with administrator and read+write permissions can connect and configure add-ons via the "Add-ons" tab in the project's navigation bar. For users
who are non-contributors and contributors with read-only permissions, the "Add-ons" tab will not be visible.

To configure an add-on, the first step is to click the **Add-ons** tab page. The "Addons" page lists all third-party services that users can connect to, including
storage providers and citation services. 

The "Add-ons" page is made up of two sections: "Select Add-ons" and "Configure Add-ons." These two sections are visible in the left sidebar menu that the user
can use to quickly navigate the page. When no add-ons have been configured, the "Select Add-ons" section is the only section on the page. However, the "Configure Add-ons"
button in the sidebar is clickable but does not lead the user anywhere on the page.

The following language appears across the top of the "Select Add-ons"::
  Sync your projects with external services to help stay connected and organized. Select a category and browse the options.

There is "Categories" sidebar menu that the user can use to filter through the add-on types: "All," "Citations," and "Storage."
"All" is selected by default. To the right of the sidebar is the list of add-ons. Each add-on has an "Enable" link to the right
of it that the user must click to initiate the connection between the add-on and their OSF project.

After enabling an add-on, the add-on will appear in the "Configure Add-ons" section.

.. _s3:

Configuring Amazon S3
*********************
**Purpose:** Connecting to Amazon S3 allows users to create a two way connection between the OSF and Amazon S3.

Clicking the **Enable** link presents the user with a modal::

    Amazon S3 Add-on Terms
    Function | Status

    Permissions: Making an OSF project public or private is independent of making an S3 bucket public or private. The
    OSF does not alter the permissions of linked S3 buckets.
    View / download file versions: The S3 add-on supports file versions if versioning is enabled for your S3 buckets.
    Add / update files: Adding/updating files in the project via OSF will be reflected in Amazon S3.
    Delete files: Files deleted via OSF will be deleted in Amazon S3.
    Logs: The OSF keeps track of changes you make to your S3 buckets through the OSF, but not for changes made using S3 directly.
    Forking: Forking a project or component does not copy S3 authorization unless the user forking the project is the
    same user who authorized the S3 add-on in the source project being forked.
    Registering: S3 content will be registered, but version history will not be copied to the registration.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions.
    The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
    [Cancel][Confirm]

On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring Box.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button::

    Settings updated

If the user has not connected Amazon S3 to their profile before, the Amazon S3 panel will then show two text fields
labeled "Access Key" and "Secret Key." The user must enter the keys and click "Save."

If the entered keys are incorrect, red inline text appears below the "Save" button::

    Unable to list buckets. Listing buckets is required permission that can be changed via IAM

If one field is left blank, red inline text appears below the "Save button::

    All the fields above are required.

After entering correct information, green inline text appears::

    Successfully added S3 credentials.

If the user has connected to Amazon S3 previously, there are no text fields but there is a blue "Import Account from Profile"
link to the right of the section title. Clicking the link opens a modal::

    Import S3 credentials?
    Are you sure you want to authorize this project with your S3 credentials?
    [Cancel][Import]

Importing refreshes the page. Green inline success text is shown in the Amazon S3 section::

    Successfully imported S3 credentials.

Below the Amazon S3 title row is now bold text that reads "Current Folder: None." This is updated when the user selects
a folder. A blue button labeled "Change" is below the "Current Folder" text. Clicking this button expands and collapses
a dropdown below. An additional button to the right of "Change" is labeled "Create Bucket."

In the dropdown are all of the user's Amazon S3 buckets. After selecting one, the user must save their changes. Leaving the page without
saving produces no warning and will not enact the changes.

Amazon's rules for bucket naming are evolving. It is possible that a previously-created bucket will violate updated bucket naming conventions. As the US East (Northern VA) region for storage was the first location, the rules for bucket naming there are more lax than other storage locations. The laxer rules allow bucket names up to 255 characters long, consisting of uppercase letters, lowercase letters, digits, periods, hyphens, and underscores. If a user attempts to connect a bucket that violates this, they will receive an error message that the bucket must follow the stricter naming conventions (though this should not be possible). See section about creating buckets (below) about bucket naming conventions.

Alternative to selecting an existing repo, the user can create a new one by clicking "Create Repo." This opens a modal::

    Bucket Name [text field]
    Bucket Location [dropdown]
    [Cancel][Create]

If the user saves an empty name field, the modal is closed and red inline text below the dropdown reads::

    Bucket name cannot be empty

Bucket names must follow Amazon's guidelines (http://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html#bucketnamingrules): Bucket names should look like subdomains, one or more labels joined with periods. A label consists of lowercase letters, numbers, and hyphens. The first and last character of a label may not be a hyphen. The bucket name must be between 3 and 63 characters long. Any character besides those are invalid.    

The "Bucket Location" field allows the user to select the server location where they wish to store their data. "US
Standard" is selected by default.

If the user correctly creates a new bucket, it becomes the choice selected in the dropdown and green inline text appears below::

    Successfully created bucket "[bucket name]". You can now select it from the drop down list.

Clicking "Save" produces green inline text below the dropdown::

    Successfully linked S3 bucket "[bucket name]". Go to the Files page to view your content.

Clicking "Save" without making changes produces no effect.

To disconnect Amazon S3, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect S3 Account?
    Are you sure you want to remove this S3 account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the dropdown and connected repo information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.


.. _box:

Configuring Box
***************
**Purpose:** Connecting to Box allows users to create a two way connection between the OSF and Box.

Clicking the **Enable** link presents the user with a modal::

    Box Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of Box privacy. The OSF does not alter the
    permissions of linked Box folders.
    View / download file versions: Box files and their versions can be viewed/downloaded via OSF.
    Add / update files: Adding/updating files in the project via OSF will be reflected in Box.
    Delete files: Files deleted via OSF will be deleted in Box.
    Logs: The OSF keeps track of changes you make to your Box content through the OSF, but not for changes made using
    Box directly.
    Forking: Forking a project or component does not copy Box authorization unless the user forking the project is the
    same user who authorized the Box add-on in the source project being forked.
    Registering: Box content will be registered, but version history will not be copied to the registration.


    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions.
    The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
    [Cancel][Confirm]

On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring Box.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button::

    Settings updated

If the user has not connected Box to their account previously, a row titled "Box" is listed in the
Configure Add-ons panel with a link—"connect account."

When users click the "connect account" link, they will be navigated to a new window where they can confirm the
connection with Box before being taken back to the Settings page on the OSF.

If the user has connected Box to their account previously, the link in the Box row reads "Import Account from Profile."
Clicking opens a modal that reads::

    Import Box Account?
    Are you sure you want to link your Box with this project?
    [Cancel][Import]

Importing or connecting an account loads the users' Box information.

To the right of the the "Box" title is text that reads::

    Box authorized by [user who configured add-on]

The "Connect Account" link is replaced by a red "Disconnect Account" link.

Below that row is bold text that reads "Current Folder: None." This is updated when the user selects a folder. A blue button labeled
"Change" is below the "Current Folder" text. Clicking this button expands and collapses a table below.

The table has two columns—"Folders" and "Select." Under "Folders" is a list of all top level Box folders the user has.
Folders can be expanded and collapsed. Each folder has a corresponding radio button in the "Select" column. When the user
selects a folder, text appears at the bottom of the table::

    Connect [folder title]?

Two buttons, "Cancel" and "Save" appear below the table. Cancelling removes the two buttons and confirmatory text but the folder
is still selected.

Clicking "Save" updates the "Current Folder" text and green inline text appears below the table, replacing the buttons::

    Successfully linked "[folder title]". Go to the Files page to view your content.

To disconnect Box, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect Box Account?
    Are you sure you want to remove this Box account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the table and connected folder information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.

.. _dataverse:

Configuring Dataverse
*********************
**Purpose:** Connecting to Dataverse allows users to create a two way connection between the OSF and Dataverse.

Clicking the **Enable** link presents the user with a modal::

    Dataverse Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of making a Dataverse study public or private. The OSF allows you to release the latest draft version of a Dataverse dataset.
    View / download file versions: Files from the latest release of the selected Dataverse study can be viewed/downloaded. OSF users with write permissions can view/download draft files as well.
    Add / update files: Adding/updating files in the project via OSF will be reflected in Dataverse.
    Delete files: Files deleted via OSF will be deleted in Dataverse.
    Logs: The OSF keeps track of changes you make to your Dataverse studies through the OSF, but not for changes made using Dataverse directly.
    Forking: Forking a project or component does not copy Dataverse authorization unless the user forking the project is the same user who authorized the Dataverse add-on in the source project being forked.
    Registering: Dataverse content will be registered, but version history will not be copied to the registration.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions.
    The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.


On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring Dataverse.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button::

    Settings updated

If the user has not connected Dataverse to their account previously, a row titled "Dataverse" is listed in the
Configure Add-ons panel with a link—"connect account."

When users click the "connect account" link, a modal opens::

    Connect a Dataverse Account
    Dataverse repository: [dropdown]
    [Cancel][Save]

The dropdown instructs users to select a Dataverse to connect. The user can make a choice from the dropdown or select "Other."
If the user selects "Other" a text field appears below the dropdown requesting a URL to the Dataverse. After a Dataverse
is indicated, a text field appears on the right for the user to enter their API Token. A link above the text field sends the user
to Dataverse where a Token is provided. The user must copy this and paste it into the field on the OSF. If a user inputs a non-dataverse URL and clicks the "Get from Dataverse" link, the user will receive a 404 error. 

If the user inputs a non-dataverse URL, no API token, and clicks "save," he receives an error, "Please enter a Dataverse host and an API token."

If the user inputs an API token and no URL and clicks, "save," he receives an error, "Please enter a Dataverse host and an API token."

If the user inputs a non-dataverse ULR and characters that are not an API token, he receives an error, "Sorry, but there was a problem connecting to that instance of Dataverse. It is likely that the instance hasn't been upgraded to Dataverse 4.0. If you have any questions or believe this to be an error, please contact support@osf.io."

.. todo:: bad error handling was fixed for user settings page, but not for project settings page. put in bug ticket.

If the user has connected Dataverse to their account previously, the link in the Dataverse row reads "Import Account from Profile."
Clicking this link opens a modal::

    Import Dataverse Access Token?
    Are you sure you want to authorize this project with your Dataverse access token?
    [Cancel][Import]

Importing or connecting an account loads the users' Dataverse information.

To the right of the the "Dataverse" title is text that reads::

    Dataverse authorized by [user who configured add-on]

The "Connect Account" link is replaced by a red "Disconnect Account" link.

Below that row is bold text that reads::

    Dataverse Repository: [connected Dataverse]

Below that is bold text that reads::
    Current Repo: None

Below this text are two dropdowns. The left dropdown ias labeled "Dataverse:" and the right "Dataset." The top choice from each
dropwdown is automatically selected.

In each dropdown are all of the user's Dataverses and Datasets belonging to the selected Dataverse. After selecting one,
the user must save their changes. Leaving the page without saving produces no warning and will not enact the changes.

Saving a change updates the "Current Dataset" field to read::

    Current Dataset: [Dataset] on [Dataverse]

Green inline text appears below the dropdowns after saving a change::

    Successfully linked dataset '[Dataset]'. Go to the Files page to view your content.

To disconnect Dataverse, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect Dataverse Account?
    Are you sure you want to remove this Dataverse account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the table and connected folder information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.

.. _dropbox:

Configuring Dropbox
*******************
**Purpose:** Connecting to Dropbox allows users to create a two way connection between the OSF and Dropbox.

Clicking the **Enable** link presents the user with a modal::

    Dropbox Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of Dropbox privacy. The OSF does not alter the permissions of linked Dropbox folders.
    View / download file versions: Dropbox files and their versions can be viewed/downloaded via OSF.
    Add / update files: Adding/updating files in the project via OSF will be reflected in Dropbox.
    Delete files: Files deleted via OSF will be deleted in Dropbox.
    Logs: OSF keeps track of changes you make to your Dropbox content through OSF, but not for changes made using Dropbox directly.
    Forking: Forking a project or component does not copy Dropbox authorization unless the user forking the project is the same user who authorized the Dropbox add-on in the source project being forked.
    Registering: Dropbox content will be registered, but version history will not be copied to the registration.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions. The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
    [Cancel][Confirm]

On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring Dropbox.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button:

    Settings updated

If the user has not connected Dropbox to their account previously, a row titled "Dropbox" is listed in the
Configure Add-ons panel with a link—"connect account."

When users click the "connect account" link, they will be navigated to a new window where they can “Allow” the connecting
of Dropbox and the OSF. Upon clicking “Allow,” users are then taken back to the Settings page on the OSF.

If the user has connected Dropbox to their account previously, the link in the Dropbox row reads "Import Account from Profile."
Clicking opens a modal that reads::

    Import Dropbox Account?
    Are you sure you want to link your Dropbox account with this project?
    [Cancel][Import]

Importing or connecting an account loads the users' Dropbox information.

To the right of the the Dropbox title is text that reads::

    Dropbox authorized by [user who configured add-on]

The "Connect Account" link is replaced by a red "Disconnect Account" link.

Below that row is bold text that reads "Current Folder: None." This is updated when the user selects a folder. A blue button labeled
"Change" is below the "Current Folder" text. Clicking this button expands and collapses a table below.

The table has two columns—"Folders" and "Select." Under "Folders" is a list of all top level Dropbox folders the user has.
Folders can be expanded and collapsed. Each folder has a corresponding radio button in the "Select" column. When the user
selects a folder, text appears at the bottom of the table::

    Connect [folder title]?

Two buttons, "Cancel" and "Save" appear below the table. Cancelling removes the two buttons and confirmatory text but the folder
is still selected.

Clicking "Save" updates the "Current Folder" text and green inline text appears below the table, replacing the buttons::

    Successfully linked "[folder title]". Go to the Files page to view your content.

To disconnect Dropbox, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect Dropbox Account?
    Are you sure you want to remove this Dropbox account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the table and connected folder information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile."

If a Dropbox account is connected, only the user who connected the account can change the selected folder. Other Admins can
remove the add-on and connect another.  Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.

.. _figshare:

Configuring figshare
********************
**Purpose:** Connecting to figshare allows users to create a two way connection between the OSF and figshare.

Refer to this `Google Doc <https://docs.google.com/document/d/1T8c69at_0X2WKficbYEV0z7bfM3jNFoWkYtmNmZjVPg/edit#heading=h.f17owbri8qc3>`_ for information on the allowable figshare actions.

Clicking the **Enable** link presents the user with a modal::

    figshare Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of making figshare content public or private. The OSF does not alter the permissions of linked figshare content.
    View / download file versions: figshare content can be viewed and downloaded via OSF provided it is "published" on figshare.
    Add / update files: Files can be added but not updated.
    Delete files: figshare files cannot be deleted via OSF.
    Logs: OSF keeps track of changes you make to your figshare content through OSF, but not for changes made using figshare directly.
    Forking: Forking a project or component does not copy figshare authorization unless the user forking the project is the same user who authorized the figshare add-on in the source project being forked.
    Registering: figshare content will be registered, but version history will not be copied to the registration.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions. The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
    [Cancel][Confirm]

On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring figshare.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button:

    Settings updated

If the user has not connected figshare to their account previously, a row titled "figshare" is listed in the
Configure Add-ons panel with a link—"connect account."

When users click the "connect account" link, they will be navigated to a new window where they can “Allow” the connecting
of figshare and the OSF. Upon clicking “Allow,” users are then taken back to the Settings page on the OSF.

If the user has connected figshare to their account previously, the link in the figshare row reads "Import Account from Profile."
Clicking opens a modal that reads::

    Import figshare Account?
    Are you sure you want to link your figshare account with this project?
    [Cancel][Import]

Importing or connecting an account loads the users' figshare information.

To the right of the the figshare title is text that reads::

    figshare authorized by [user who configured add-on]

The "Connect Account" link is replaced by a red "Disconnect Account" link.

Below that row is bold text that reads "Current Folder: None." This is updated when the user selects a folder. A blue button labeled
"Change" is below the "Current Folder" text. Clicking this button expands and collapses a table below.

The table has two columns—"Folders" and "Select." Under "Folders" is a list of all top level figshare folders the user has.
Folders can be expanded and collapsed. Each folder has a corresponding radio button in the "Select" column. When the user
selects a folder, text appears at the bottom of the table::

    Connect [folder title]?

Two buttons, "Cancel" and "Save" appear below the table. Cancelling removes the two buttons and confirmatory text but the folder
is still selected.

Clicking "Save" updates the "Current Folder" text and green inline text appears below the table, replacing the buttons::

    Successfully linked "[folder title]". Go to the Files page to view your content.

To disconnect figshare, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect figshare Account?
    Are you sure you want to remove this figshare account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the table and connected folder information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile."

If a figshare account is connected, only the user who connected the account can change the selected folder. Other Admins can
remove the add-on and connect another.  Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.


.. _github:

Configuring GitHub
******************
**Purpose:** Connecting to GitHub allows users to create a two way connection between the OSF and GitHub.

Clicking the **Enable** link presents the user with a modal::

    GitHub Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of making a GitHub repo public or private.
    The OSF does not alter the permissions of linked GitHub repos.
    View / download file versions: GitHub files and their versions can be viewed/downloaded via OSF.
    Add / update files: Adding/updating files in the project via OSF will be reflected in GitHub.
    Delete files: Files deleted via OSF will be deleted in GitHub.
    Logs: GitHub dynamically updates OSF logs when files are modified outside the OSF. Changes to GitHub repos made before
    the repo is linked to the OSF will not be reflected in OSF logs.
    Forking: Forking a project or component does not copy Github authorization unless the user forking the project is the
    same user who authorized the Github add-on in the source project being forked.
    Registering: GitHub content will be registered, but version history will not be copied to the registration.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions.
    The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.


On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring GitHub.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button::

    Settings updated

If the user has not connected GitHub to their account previously, a row titled "GitHub" is listed in the
Configure Add-ons panel with a link—"connect account."

When users click the "connect account" link, they will be navigated to a new window where GitHub authenticates the connection.
After authorizing, the user is returned to the OSF.

If the user has connected GitHub to their account previously, the link in the GitHub row reads "Import Account from Profile."

After authorizing GitHub or clicking the **Import Account from Profile** link, the user will see a modal, asking to confirm importing their GitHub content into OSF::
  
    Import GitHub Account?
    Are you sure you want to link your GitHub account with this project?
    [Cancel][Import]

Clicking the **Import** button imports the user's GitHub content. The GitHub connection will appear in the "Configure Add-ons" section of the page. Below GitHub is a blue dismissible banner that instructs users on what to do if their GitHub organizations do not load::
  
    Don't see your GitHub organization repositories?
    You may need to reauthorize your GitHub access token. Follow the steps in the help guide <http://help.osf.io/a/850865-reauthorize-github> to resolve the issue.
    Please contact support@osf.io if you have questions.

To the right of the the "GitHub" title is text that reads::

    GitHub authorized by [user who configured add-on]

The "Connect Account" link is replaced by a red "Disconnect Account" link.

Below that row is bold text that reads "Current Repo:" Below this text is a dropdown that shows "------" by default.
To the right of the dropdown is a green button that reads "Create Repo." On the far right of this row is a green "Save" button.

In the dropdown are all of the user's GitHub repos. After selecting one, the user must save their changes. Leaving the page without
saving produces no warning and will not enact the changes.

Alternative to selecting an existing repo, the user can create a new one by clicking "Create Repo." This opens a modal::

    Name your new repo
    [text field]
    [Cancel][Save]

If the user saves an empty name field, the modal is closed and red inline text below the dropdown reads::

    Error: Your repo must have a name

If the user correctly enters a name, it becomes the choice selected in the dropdown.


Clicking "Save" produces green inline text below the dropdown::

    Settings updated

Clicking "Save" without making changes produces no effect.

To disconnect GitHub, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect GitHub Account?
    Are you sure you want to remove this GitHub account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the dropdown and connected repo information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.

.. _gitlab:

Configuring GitLab
******************
**Purpose:** Connecting to GitLab allows users to create a two way connection between the OSF and GitLab.

Users who choose to connect their GitLab account to the OSF can check appropriate box. They are presented with a
modal::

  GitLab Add-on Terms
  Function | Status
  Permissions	| Making an OSF project public or private is independent of making a GitLab repo public or private. The OSF does not alter the permissions of linked GitLab repos.
  View / download file versions |	GitLab files and their versions can be viewed/downloaded via OSF.
  Add / update files | Adding/updating files in the project via OSF is not implemented yet.
  Delete files	| Deleting files via OSF is not implemented yet.
  Logs | OSF does not keep track of changes made using Gitlab directly.
  Forking	| Forking a project or component does not copy GitLab authorization unless the user forking the project is the same user who authorized the GitLab add-on in the source project being forked.
  Registering	| GitLab content will be registered, but version history will not be copied to the registration.
  This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions. The OSF is not responsible for the service or for your use thereof.
  This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
  [Cancel][Confirm]
  
On this modal, users can click “Cancel” to cancel this action and close the modal or click “Confirm” to continue configuring GitLab.

If the user clicks **Confirm** the modal closes, and GitLab appears in the "Configure Add-ons" section. If the user does not have GitLab connected in their user Settings, a "Connect Account" link is listed beside GitLab. Clicking this link brings up the following modal::
  
  Connect a GitLab Account
  GitLab Repository 
  [menu]
  [Cancel] [Save]
  
The text inside the menu reads: Select a GitLab repository. Clicking inside this menu shows two options::

  gitlab.com
  Other (Please specify)
  
Clicking **Cancel** closes the modal. Clicking **Save** without choosing a repository causes a red error message to appear below the menu::
  
    Please select a GitLab repository.

Clicking **gitlab.com** causes a second field to apepar on the right side of the modal::
  
    Personal Access Token (Get from GitLab)
    [field]

Clicking **Save** without entering personal access token causes a red error message to appear below the repository menu::
    
    Please enter your Personal Access Token.

Clicking the **Get from GitLab** link takes the user to the GitLab "Sign in" page. 
If the user is already signed in to GitLab, clicking the link takes them to their "Personal Access Tokens" page.

When the user enters their token into the modal and clicks **Save**, the modal closes, and the following one opens::
  
  Import GitLab Account?
  Are you sure you want to link your GitLab account with this project?
  [Cancel][Import]

Clicking **Cancel** closes the modal. Clicking **Import** closes the modal, the page reloads, and the user's GitLab account is imported into the project. A drop-down menu appears with the user's GitLab repositories in the "Configure Add-ons" section::
  
  GitLab authorized by Rebecca Rosenblatt Disconnect Account
  Current Repo:
  [menu] [Save]
  
After choosing a repository from the menu, the user can click **Save**. A green confirmation message appears below the "Configure Add-ons" section::
  
  Settings updated

After importing their account, the user will see a red "Disconnect Account" link to the right of the drop-down section. 

Clicking this link opens a modal::

  Disconnect GitLab Account?
  Are you sure you want to remove this GitLab account?
  [Cancel][Disconnect]

Clicking "Disconnect" removes GitLab and connected GitLab information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.

The user can change the folder connected to the project. Below the GitLab section below "Configure Add-ons", there is a menu with the available repos with a green "Save" button the the right. To select a new folder, the user clicks inside the repo menu, selects a different folder, then clicks **Save**. A confirmation message appears below the menu::
  
   Settings updated

.. _drive:

Configuring Google Drive
************************
**Purpose:** Connecting to Google Drive allows users to create a two way connection between the OSF and Google Drive.

Clicking the **Enable** link presents the user with a modal::

    Google Drive Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of Google Drive privacy. The OSF does not alter the
    permissions of linked Google Drive folders.
    View / download file versions: Google Drive files and their versions can be viewed/downloaded via OSF.
    Add / update files: Adding/updating files in the project via OSF will be reflected in Google Drive.
    Delete files: Files deleted via OSF will be deleted in Google Drive.
    Logs: The OSF keeps track of changes you make to your Google Drive content through the OSF, but not for changes made using
    Google Drive directly.
    Forking: Forking a project or component does not copy Google Drive authorization unless the user forking the project is
    the same user who authorized the Google Drive add-on in the source project being forked.
    Registering: Google Drive content will be registered, but version history will not be copied to the registration.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions. The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
    [Cancel][Confirm]

On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring Google Drive.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button:

    Settings updated

If the user has not connected Google Drive to their account previously, a row titled "Google Drive" is listed in the
Configure Add-ons panel with a link—"connect account."

When users click the "connect account" link, they will be navigated to a new window where they can “Accept” the terms &
conditions of connecting Google Drive to the OSF. Upon clicking “Accept,” users are then taken back to the Settings
page on the OSF.

If the user has connected Google Drive to their account previously, the link in the Google Drive row reads "Import Account from Profile."
Clicking opens a modal that reads::

    Import Google Drive Account?
    Are you sure you want to link your Google Drive account with this project?
    [Cancel][Import]

Importing or connecting an account loads the users' Google Drive information.

To the right of the the "Google Drive" title is text that reads::

    Google Drive authorized by [user who configured add-on]

The "Connect Account" link is replaced by a red "Disconnect Account" link.

Below that row is bold text that reads "Current Folder: None." This is updated when the user selects a folder. A blue button labeled
"Change" is below the "Current Folder" text. Clicking this button expands and collapses a table below.

The table has two columns—"Folders" and "Select." Under "Folders" is a list of all top level Google Drive folders the user has.
Folders can be expanded and collapsed. Each folder has a corresponding radio button in the "Select" column. When the user
selects a folder, text appears at the bottom of the table::

    Connect [folder title]?

Two buttons, "Cancel" and "Save" appear below the table. Cancelling removes the two buttons and confirmatory text but the folder
is still selected.

Clicking "Save" updates the "Current Folder" text and green inline text appears below the table, replacing the buttons::

    Successfully linked "[folder title]". Go to the Files page to view your content.

To disconnect Google Drive, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect Google Drive Account?
    Are you sure you want to remove this Google Drive account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the table and connected folder information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.


.. _onedrive:

Configuring OneDrive
**Purpose**: Connecting to OneDrive allows users to create a two way connection between the OSF and OneDrive.

Users who choose to connect their Mendeley account to the OSF can check the appropriate box. They are presented with a
modal::
  
  OneDrive Add-on Terms
  Function	| Status
  Permissions:	Making an OSF project public or private is independent of OneDrive privacy. The OSF does not alter the permissions of linked OneDrive folders.
  View / download file versions	OneDrive files and their versions can be viewed/downloaded via OSF. OneNote files are unexportable and cannot be downloaded or viewed.
  Add / update files	The OneDrive add-on is read-only.
  Delete files	The OneDrive add-on is read-only.
  Logs	OSF keeps track of changes you make to your OneDrive add-on configuration. It does not track changes to OneDrive content.
  Forking: Forking a project or component does not copy OneDrive authorization unless the user forking the project is the same user who authorized the OneDrive add-on in the source project being forked.
  Registering	OneDrive content will be registered, but version history will not be copied to the registration. OneNote files are unexportable and will not be archived.

  This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions. The OSF is not responsible for the service or for your use thereof.
  This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.

On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring OneDrive.

After confirming, OneDrive will appear in the "Configure Add-ons" section of the page. If the user has never connected OneDrive to their project or account, they will see a blue "Connect Account" link to the right of OneDrive. Clicking **Connect Account** takes the user
to the Microsoft "Sign In" page, where they will need to enter their Microsoft username and password. After entering the login credentials, they will be taken back to their OSF project's "Add-ons" page, where a list of their OneDrive folders will be listed
in the "Configure Add-ons" section, and a red "Disconnect Account" link appears to the right of OneDrive. 

The table has two columns—"Folders" and "Select." Under "Folders" is a list of all top level OneDrive folders the user has. Folders can be expanded and collapsed.
Each folder has a corresponding radio button in the "Select" column. When the use selects a folder, text appears at the bottom of the table::
  
    Connect "[folder name]"?

Two buttons, "Cancel" and "Save" appear below the table. Clicking **Cancel** removes the two buttons, while the folder remains selected.

Clicking **Save** connects the selected folder to the project, and a green inline confirmation message appears below the table, replacing the buttons::

    Successfully linked "[folder title]". Go to the Files page [links to https://osf.io/GUID/files/] to view your content.

To disconnect OneDrive, the user clicks the red "Disconnect Account" link. This opens a modal::
  
  Disconnect Microsoft OneDrive Account?
  Are you sure you want to remove this Microsoft OneDrive account?
  [Cancel][Disconnect]

Clicking **Cancel** keeps OneDrive connected. Clicking **Disconnect** removes the table and connected folder information, and a temporary inline confirmation message appears below OneDrive::
  
    Disconnected Microsoft OneDrive.  
    
The "Disconnect Account" link is replaced by a link that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.


The user can change the folder connected to the project. In the "OneDrive" section below "Configure Add-ons", there is a blue "Change" button. Clicking **Change** opens a table that displays the OneDrive folders. The table
has two columns "Folders" and "Select". Below "Select" is a column of radio buttons. To change the folder, the users selects a new folder, which causes "Cancel" and "Save" buttons to appear at the bottom of the page. Above
these buttons is a blue message::
  
    Connect "[folder name]"
    
Clicking **Save** changes the folder.


.. _mendeley:

Configuring Mendeley
********************
**Purpose:** Connecting to Mendeley allows users to create a two way connection between the OSF and Mendeley.

Clicking the **Enable** link presents the user with a modal::

    Mendeley Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of making a Mendeley folder public or private.
    The OSF does not alter the permissions of a linked Mendeley folder.
    Forking: Forking a project or component does not copy Mendeley authorization unless the user forking the project is
    the same user who authorized the Mendeley add-on in the source project being forked.
    Registering: Mendeley content will not be registered.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions.
    The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
    [Cancel][Confirm]

On this modal, users can click “Cancel” to cancel this action and close the window or “Confirm” to continue configuring Box.

If user clicks “Confirm” but does not click “Apply,” and navigates away from page, a browser popup appears asking user to
confirm navigation away from the page because pending add-on changes were not saved.

After confirming, users will see a green “Apply” button appear at the bottom of the Select Add-ons panel. Clicking “Apply”
will apply the settings. Green inline text appears for a few seconds below the "Apply" button::

    Settings updated

If the user has not connected Mendeley to their account previously, a row titled "Mendeley" is listed in the
Configure Add-ons panel with a link—"connect account."

When users click the "connect account" link, they will be navigated to a new window where they can confirm the
connection with Mendeley before being taken back to the Settings page on the OSF. When they return to the OSF a modal appears::

    Import Mendeley access token
    Are you sure you want to link your Mendeley account with this project?
    [Cancel][Import]

If the user has connected Mendeley to their account previously, the link in the Mendeley row reads "Import Account from Profile."
Clicking opens a modal that reads::

    Import Mendeley access token
    Are you sure you want to link your Mendeley account with this project?
    [Cancel][Import]

Importing an account loads the users' Mendeley information.

To the right of the the Mendeley title is text that reads::

    authorized by [user who configured add-on]

The "Connect Account" link is replaced by a red "Disconnect Account" link.

Below that row is bold text that reads "Current Folder: None." This is updated when the user selects a folder. A blue button labeled
"Change" is below the "Current Folder" text. Clicking this button expands and collapses a table below.

The table has two columns—"Folders" and "Select." Under "Folders" is a list of all top level Mendeley folders the user has.
Folders can be expanded and collapsed. Each folder has a corresponding radio button in the "Select" column. When the user
selects a folder, text appears at the bottom of the table::

    Connect [folder title]?

Two buttons, "Cancel" and "Save" appear below the table. Cancelling removes the two buttons and confirmatory text but the folder
is still selected.

Clicking "Save" updates the "Current Folder" text and green inline text appears below the table, replacing the buttons::

    Successfully linked "[folder title]". Go to the Overview page to view your citations.

To disconnect Mendeley, the user clicks the red "Disconnect Account" link. This opens a modal::

    Disconnect Mendeley Account?
    Are you sure you want to remove this Mendeley account?
    [Cancel][Disconnect]

Clicking "Disconnect" removes the table and connected folder information. The "Disconnect Account" link is replaced by a link
that reads "Import Account from Profile." Alternatively, the user can uncheck the add-on from the "Select Add-ons" list and save their
changes.

.. _zotero:

**Purpose**: Connecting to Zotero allows users to create a two-way connection between the OSF and Zotero.

Clicking the **Enable** link presents the user with a modal::

    Zotero Add-on Terms
    Function | Status
    Permissions: Making an OSF project public or private is independent of making a Zotero folder public or private.
    The OSF does not alter the permissions of a linked Zotero folder.
    Forking: Forking a project or component does not copy Zotero authorization unless the user forking the project is
    the same user who authorized the Zotero add-on in the source project being forked.
    Registering: Zotero content will not be registered.

    This add-on connects your OSF project to an external service. Use of this service is bound by its terms and conditions.
    The OSF is not responsible for the service or for your use thereof.
    This add-on allows you to store files using an external service. Files added to this add-on are not stored within the OSF.
    [Cancel][Confirm]
    
Clicking **Cancel** cancels this action and closes the modal. Clicking **Confirm** sets up the Zotero configuration.

After confirming, Zotero will appear in the "Configure Add-ons" section below the "Select Add-ons" section. A blue box appears below Zotero to instructs users on what to do if they do not see their Zotero libraries::
  
  Don’t see your Zotero group libraries?
  You may need to reauthorize your Zotero access token. Follow the steps in the help guide to resolve the issue.  
  Please contact support@osf.io if you have questions.

The text "help guide" links to this help guide: http://help.osf.io/a/850167-reauthorize-zotero.

If the user has not previously connected Zotero to their account, they will see a "Connect account" link. Clicking **Connect account** will take the user to Zotero where they will need to authorize OSF access to their Zotero content. After granting access to OSF, the user will be taken back to their OSF "Add-ons" page, where they will see a modal in which they will need to import their Zotero access token::

    Import Zotero access token
    Are you sure you want to link your Zotero account with this project?
    [Cancel][Import]
    
If the user has previously connected Zotero to their account, the link in the Zotero row will read "Import Account from Profile." Clicking this link opens the "Import Zotero access token" modal.
    
After the user clicks **Import**, a temporary green, inline confirmation message appears above the blue box::
  
    Successfully imported Zotero account from profile

The user can then select the library that they want to connect to their project::

    Current Library: None
    [Change]

Clicking the **Change** button opens a table of the user's individual and group libaries::
  
    Libraries | Select
    
Clicking the radio button next to a library selects the library, and shows "Cancel" and "Save" buttons below the table. Clicking **Cancel** hides these buttons, while the library remains selected. Clicking **Save** shows a green, inline confirmation message above the blue box::
  
    Successfully linked "<library>". Next, choose which folder to link above.

The "Current Library" field will read::
  
    Current Library: <library>

The user can then select the folder within the library that they want to connect to their project::
  
    Current Folder: None
    [Change]

Clicking the **Change** button opens a table of the user's library folders::
  
      Folders | Select

Clicking the radio button next to a library selects the library. The user can choose to select **All Documents** to connect all their folders to their project. After selecting a folder, a blue message appears below the table::
  
    Connect "<folder>"?

"Cancel" and "Save" buttons also appear below the table. Clicking **Cancel** hides these buttons. Clicking **Save** connects the selected library and folder to the user's project. A green, inline confirmation message appears above the blue box::
  
    Successfully linked "<folder>". Go to the Overview page to view your citations.

The text "Overview page" links to the project Overview page.

To disconnect Zotero from their project, the user must click the red **Disconnect Account** link. Clicking this link opens a confirmation modal::
    
    Disconnect Zotero Account?
    Are you sure you want to remove this Zotero account?
    [Cancel][Disconnect]
    
Clicking **Cancel** cancels the action and closes the modal. Clicking **Disconnect** disconnects the user's library and folder from their project. The "Disconnect Account" link is replaced by a link that reads "Import Account from Profile." A temporary, yellow confirmation message appears above the blue box::
  
    Disconnected Zotero
 
To remove the Zotero configuration, the user can click the **Disable** link next to Zotero in the "Select Add-ons" list. Clicking this link opens a modal::
  
  Disable Add-on?
  Are you sure you want to disable this add-on?
  [Cancel][Disable]
  
Clicking **Cancel** cancels the action and closes the modal. Zotero will remain in the "Configure Add-ons" section. Clicking **Disable** removes Zotero from the ""Configure Add-ons" section, and replaces the red "Disable" link with the green "Enable" link in the "Select Add-ons" section.

Viewing Amazon S3 Files
***********************
**Purpose:** The file tree and file details pages allow users to view and interact with Amazon S3 files.

Amazon S3 appears in in the file tree as an item in the component to which it has been added. It is on the same level as OSF Storage.
The tree identifies the project::

    Amazon S3: [bucket name]

File names from an Amazon S3 bucket are shown in the file tree on the OSF.

Selecting the Amazon S3 add-on in the file tree shows a "Download as zip" button in the toolbar. Clicking downloads the entire
contents of the bucket as a zip folder.

A "Create Folder" button is also shown when the add-on is selected. The user types a folder name and confirms creation. The folder
is then shown inside the Amazon S3 add-on. Files can be moved into and out of the folder. Folders can be removed by selecting the
folder and clicking "Delete Folder" in the toolbar. A modal opens::

    Delete "folder"?
    This folder and ALL its contents will be deleted. This action is irreversible.
    [Cancel][Delete]

Users with editing permissions can select an Amazon S3 file to rename it. Clicking the "Rename" button that appears in the file
tree's toolbar opens a text box where the new name can be entered and saved.

When a user with editing permissions selects Amazon S3 in the file tree, an “Upload” button appears. Clicking on “Upload”
opens a modal that allows you to select files from within your computer to upload. Admins and read+write contributors
can also drag and drop files onto the Amazon S3 add-on to upload a file.

If a new version of an already existent file is uploaded, the new version will replace the existing one.

If an Amazon S3 file is selected by a user, a "View" button appears in the toolbar. Clicking this button or clicking the file title
brings the user to the details (rendering) page where the file is rendered. No link is provided to view the file on Amazon S3.

On the file's detail page, the image is rendered in the default "view" pane. Users with editing permissions see a "Delete"
button in the top right.

    Delete file?
    Are you sure you want to delete [file name]?
    [Cancel][Delete]

Confirming the deletion brings the user to the file tree page where that file has been removed.

A blue "Download" button is also available on the detail page. Clicking downloads the file.

Text and code files can be edited from the file detail page by users with edit permissions. Clicking "Edit" opens a pane
to the right of the rendered text where the user can revise the contents of the file. Saving updates the contents of the file.
Edits are not rendered in the view of the file on the left. No formatting options are available.

Selecting the "Revisions" button on the detail page opens the revisions pane. Only the most recent version of the Amazon S3 file
is listed. The date of the upload is available, and a download button is shown on the right side of the pane.

Selecting a file from the file tree shows a "Download" button in the toolbar.  No "Download Multiple" button
is ever available, even if multiple Amazon S3 files are selected. Download counts are not available for Amazon S3.

If the user has editing privileges, clicking on an Amazon S3 file in the file tree shows a "Delete" button in the toolbar.
Clicking this button opens a modal::

    Delete "[file title]"?
    This action is irreversible.
    [Cancel][Delete]

If the user selects multiple files, a "Delete Multiple" button appears in the toolbar. Clicking opens a modal::

    Delete "[file title]"?
    This action is irreversible.

    [list of file titles]

    [Cancel][Delete]

After confirming, the files are removed from the OSF and Amazon S3.

Files from other storage add-ons can be moved into Amazon S3 by dragging and dropping. Files from Amazon S3 can be moved
into other add-ons as well.

Viewing OneDrive Files
**********************
**Purpose**: The file tree and file details pages allow users to view and interact with OneDrive files. The connection between OneDrive and the OSF is read-only.

OneDrive appears in in the file tree as a storage provider that is on the same level as OSF Storage::

    OneDrive: "[Folder name]"

File and folder names from the connected OneDrive folder are shown in the file tree on the OSF project.

Selecting OneDrive or a OneDrive subfolder in the file tree shows a "Download as zip" button in the toolbar. Clicking **Download as zip** downloads the entire
contents of the folder as a zip folder.

If a OneDrive file is selected by a user, "Download," "View," and "View on OneDrive" buttons appear in the toolbar. Clicking **Download** downloads the file. Clicking **View** takes the user to "File Detail" page. 
Clicking **View on OneDrive** opens the file in OneDrive where the user can view it. 

On the "File Detail" page, the file is rendered in the default "view" pane. A blue "Download" and "View" button appears in the toolbar, along with a "Revisions" button. 
Clicking **Download** downloads the file. The "View" and "Revisions" buttons are toggled, where "View" is selected by default. Clicking **Revisions** highlights the
button in blue and the "View" button in white, and the revision history for the file replaces the rendered file. The date of the revision is available, and a "Download" button is shown on the right side of the pane.


Files from OneDrive can be dragged annd dropped into other storage providers, but files from other storage providers cannot be added to OneDrive. 

Viewing Box Files
*****************
**Purpose:** The file tree and file details pages allow users to view and interact with Box files.

Box appears in in the file tree as an item in the component to which it has been added. It is on the same level as OSF Storage.
The tree identifies the project::

    Box: [folder name]

File names from the indicated Box folder are shown in the file tree on the OSF.

Selecting the Box add-on in the file tree shows a "Download as zip" button in the toolbar. Clicking downloads the entire
contents of the folder as a zip file.

A "Create Folder" button is also shown when the add-on is selected. The user types a folder name and confirms creation. The folder
is then shown inside the Box add-on. Files can be moved into and out of the folder. Folders can be removed by selecting the
folder and clicking "Delete Folder" in the toolbar. A modal opens::

    Delete "folder"?
    This folder and ALL its contents will be deleted. This action is irreversible.
    [Cancel][Delete]

Users with editing permissions can select a Box file to rename it. Clicking the "Rename" button that appears in the file
tree's toolbar opens a text box where the new name can be entered and saved.

When a user with editing permissions selects Box in the file tree, an “Upload” button appears. Clicking on “Upload”
opens a modal that allows you to select files from within your computer to upload. Admins and read+write contributors
can also drag and drop files onto the Box add-on to upload a file.

If a new version of an already existent file is uploaded, the new version will replace the existing one.

If a Box file is selected by a user, a "View" button appears in the toolbar. Clicking this button or clicking the file title
brings the user to the details (rendering) page where the file is rendered. No link is provided to view the file on Box.

On the file's detail page, the image is rendered in the default "view" pane. Users with editing permissions see a "Delete"
button in the top right.

    Delete file?
    Are you sure you want to delete [file name]?
    [Cancel][Delete]

Confirming the deletion brings the user to the file tree page where that file has been removed.

A blue "Download" button is also available on the detail page. Clicking downloads the file.

Text and code files can be edited from the file detail page by users with edit permissions. Clicking "Edit" opens a pane
to the right of the rendered text where the user can revise the contents of the file. Saving updates the contents of the file.
No formatting options are available.

Selecting the "Revisions" button on the detail page opens the revisions pane. Only the most recent version of the Box file
is listed. The date of the upload is available, and a download button is shown on the right side of the pane.

Selecting a file from the file tree shows a "Download" button in the toolbar.  No "Download Multiple" button
is ever available, even if multiple Box files are selected. Download counts are not available for Box.

If the user has editing privileges, clicking on a Box file in the file tree shows a "Delete" button in the toolbar.
Clicking this button opens a modal::

    Delete "[file title]"?
    This action is irreversible.
    [Cancel][Delete]

If the user selects multiple files, a "Delete Multiple" button appears in the toolbar. Clicking opens a modal::

    Delete "[file title]"?
    This action is irreversible.

    [list of file titles]

    [Cancel][Delete]

After confirming, the files are removed from the OSF and Box.

Files from other storage add-ons can be moved into Box by dragging and dropping. Files from Box can be moved
into other add-ons as well.

Viewing Dataverse Files
***********************
**Purpose:** The file tree and file details pages allow users to view and interact with Dataverse files.

Dataverse appears in in the file tree as an item in the component to which it has been added. It is on the same level as OSF Storage.
The tree identifies the project::

    Dataverse: [Dataset name] (Draft)[Draft]

File names from the indicated Dataset are shown in the file tree on the OSF. By default, the draft Dataset is shown.

Selecting the Dataverse add-on in the file tree shows a dropdown in the toolbar titled "Version:" From the dropdown, the user can
select the published Dataset or the draft Dataset. Changing the selection will show the appropriate Dataset. User will only see the options relevant to the dataset (if there is no draft version, only "published" will display, and vice versa).

When the add-on is selected and the Dataverse and Dataset have not been published, a "Publish" button is shown in the toolbar.
Clicking opens a modal::

    Publish this Dataverse and dataset?
    This dataset cannot be published until [Dataverse title] is published.
    By publishing this Dataverse and dataset, all content will be made available through the Harvard Dataverse
    using their internal privacy settings, regardless of your OSF project settings.
    Do you want to publish this Dataverse AND this dataset?

    [Cancel][Publish Dataverse and dataset]

When the add-on is selected and the Dataverse  has been published but the Dataset has not, a "Publish" button is shown in the toolbar.
Clicking opens a modal::

    Publish this Dataverse and dataset?
    By publishing this dataset, all content will be made available through the Harvard Dataverse using their internal
    privacy settings, regardless of your OSF project settings.
    Are you sure you want to publish this dataset?

    [Cancel][Publish dataset]

Confirming the choice to publish opens another modal::

    Your content has been published.
    [Okay]

When a draft dataset is selected, the "Publish" button is available even if it has been published. If the user clicks "Publish"
for a draft that has been published, the confirmation modal appears. On confirming, another modal appears::

    This dataset version has already been published.
    [Okay]

When a draft dataset from a published Dataverse is selected, the add-on row in the file tree reads::

    Dataverse: [Dataset] (Draft)

When a published dataset from a published Dataverse is selected, the add-on row in the file tree reads::

    Dataverse: [Dataset] (Published)

"Version:" dropdown is available for published Datasets, but no other add-on specific buttons are available in the toolbar.

If the user selects a published file in the file tree, a "Download" button is added to the toolbar. Clicking will download the
file. No "Download Multiple" button is ever available, even if multiple Dataverse files are selected. Download
counts are not available for Dataverse.

No "Upload" is available for published Datasets. Attempting to drag and drop onto a published dataset produces no action.

On the file tree, when a draft Dataset is selected by a contributor with editing privileges, an "Upload" button is
available in the toolbar to the left of the "Publish" button. Clicking opens the file selector. Files can also be
dragged and dropped into the file tree by users with editing privileges.

If a file cannot be uploaded, a red growlbox error shows in the upper right corner::

    Error
    Unable to reach the provider, please try again later. If the problem persists, please contact support@osf.io.

Even if an error was shown, if the user refreshes, the file may be uploaded to the draft Dataverse.

Files from other storage add-ons cannot be moved into Dataverse, nor can any Dataverse files be moved out.

If a new version of an already existent file is uploaded, the versions will not combine. Two identically titled files will be shown;
on refresh, the newer file will have an integer appended to the end to identify it as a subsequent copy.

If the user has editing privileges, clicking on a draft Dataverse file in the file tree shows a "Delete" button in the toolbar.
Clicking this button opens a modal::

    Delete "[file title]"?
    This action is irreversible.
    [Cancel][Delete]

If the user selects multiple draft files, a "Delete Multiple" button appears in the toolbar. Clicking opens a modal::

    Delete "[file title]"?
    This action is irreversible.

    [list of file titles]

    [Cancel][Delete]

After confirming, the files are removed from the OSF and Dataverse.

If any Dataverse file is selected by a user in the file tree, a "View" button appears in the toolbar. Clicking this button or clicking the file title
brings the user to the details (rendering) page where the file is rendered. No link is provided to view the file on Dataverse.

When viewing the detail page of a published file, a red "Delete" button is available in the top right. Clicking this button results
in a red growlbox error::

    Error
    Could not delete file

Draft files can be deleted. Clicking "Delete" opens a confirmation modal::

    Delete file?
    Are you sure you want to delete [file name]?
    [Cancel][Delete]

Confirming the deletion brings the user to the file tree page where that file has been removed.

A blue "Download" button is also available on the detail page. Clicking downloads the file.

The revisions view shows up to two versions: published and draft. The options present depend on if the file has ever been published and
if a draft version has been deleted. Clicking on the draft version shows the draft of the file, clicking on published shows the published version.
The "Delete" and "Download" buttons are available on the detail page for both published and draft files.

From the detail page of a file, the left hand panel displaying the file tree will show the Dataset that the viewed file belongs to—
draft or published. If the user visits a different version by selecting it in the revisions pane, the file tree will update to reflect
the current dataset.

To non-contributors, draft Dataverse files cannot be seen. If a dataset is completely unpublished, this means that the Dataverse add-on
does not appear in the file tree. Published files can be viewed and downloaded.


Viewing Dropbox Files
*********************
**Purpose:** The file tree and file details pages allow users to view and interact with Dropbox files.

Dropbox appears in in the file tree as an item in the component to which it has been added. It is on the same level as OSF Storage.
The tree identifies the project::

    Dropbox: /[folder name]

File names from the indicated Dropbox folder are shown in the file tree on the OSF.

Selecting the Dropbox add-on in the file tree shows a "Download as zip" button in the toolbar. Clicking downloads the entire
contents of the folder as a zip file.

A "Create Folder" button is also shown when the add-on is selected. The user types a folder name and confirms creation. The folder
is then shown inside the Dropbox add-on. Files can be moved into and out of the folder. Folders can be removed by selecting the
folder and clicking "Delete Folder" in the toolbar. A modal opens::

    Delete "folder"?
    This folder and ALL its contents will be deleted. This action is irreversible.
    [Cancel][Delete]

Users with editing permissions can select a Dropbox file to rename it. Clicking the "Rename" button that appears in the file
tree's toolbar opens a text box where the new name can be entered and saved.

When a user with editing permissions selects Dropbox in the file tree, an “Upload” button appears. Clicking on “Upload”
opens a modal that allows you to select files from within your computer to upload. Admins and read+write contributors
can also drag and drop files onto the Box add-on to upload a file.

If a new version of an already existent file is uploaded, the new version will replace the existing one.

If a Dropbox file is selected by a user, a "View" button appears in the toolbar. Clicking this button or clicking the file title
brings the user to the details (rendering) page where the file is rendered. No link is provided to view the file on Dropbox.

On the file's detail page, the image is rendered in the default "view" pane. Users with editing permissions see a "Delete"
button in the top right.

    Delete file?
    Are you sure you want to delete [file name]?
    [Cancel][Delete]

Confirming the deletion brings the user to the file tree page where that file has been removed.

A blue "Download" button is also available on the detail page. Clicking downloads the file.

Text and code files can be edited from the file detail page by users with edit permissions. Clicking "Edit" opens a pane
to the right of the rendered text where the user can revise the contents of the file. Saving updates the contents of the file.
No formatting options are available.

Selecting the "Revisions" button on the detail page opens the revisions pane. Revisions from the last 30 days are available.
The date of upload for each version is shown, and a download button is shown on the right side of the pane.

Selecting a file from the file tree shows a "Download" button in the toolbar.  No "Download Multiple" button
is ever available, even if multiple Dropbox files are selected. Download counts are not available for Dropbox.

If the user has editing privileges, clicking on a Dropbox file in the file tree shows a "Delete" button in the toolbar.
Clicking this button opens a modal::

    Delete "[file title]"?
    This action is irreversible.
    [Cancel][Delete]

If the user selects multiple files, a "Delete Multiple" button appears in the toolbar. Clicking opens a modal::

    Delete "[file title]"?
    This action is irreversible.

    [list of file titles]

    [Cancel][Delete]

After confirming, the files are removed from the OSF and Dropbox.

Files from other storage add-ons can be moved into Dropbox by dragging and dropping. Files from Dropbox can be moved
into other add-ons as well.

From the :ref:`project overview <overview>` a Dataverse panel is visible below the file tree. The panel displays four
fields: Dataset, Global ID, Dataverse, and Citation. The titles and DOI assigned by Dataverse are available in the appropriate fields.
The citation generated by Dataverse is available in the Citation field. The DOI ("Global ID") and Dataverse fields
link to the dataset on the Dataverse website.


Viewing figshare Files
**********************
**Purpose:** The file tree and file details pages allow users to view and interact with figshare files.

Refer to this `Google Doc <https://docs.google.com/document/d/1T8c69at_0X2WKficbYEV0z7bfM3jNFoWkYtmNmZjVPg/edit#heading=h.f17owbri8qc3>`_ for more information on allowabel figshare actions

figshare appears in in the file tree as an item in the component to which it has been added. It is on the same level as OSF Storage.
The tree identifies the project::

    figshare: [project title]

File names from a figshare project are shown in the file tree on the OSF—not the names assigned to them on figshare. Names of
both published, public files and private, draft files are shown in the tree. figshare files cannot be renamed. Folders cannot
be created within the figshare add-on.

If an OSF project is private and figshare is connected, a nondismissable blue alert is visible at the top of each page, regardless
of the privacy of the figshare files::

    Warning: This OSF component is private but figshare project 5022 may contain some public files or filesets.

If the OSF project is public, no alert is shown, regardless of the privacy of the figshare files. The titles of all figshare files are shown
in public projects.

If a figshare project is deleted from the figshare website, it no longer appears in the file tree, but is still visible as the
selected project on the project settings page.

When a user with admin or read+write permissions selects figshare in the file tree a “Upload” button appears. Clicking on “Upload”
opens a modal that allows you to select files from within your computer to upload. Admins and read+write contributors
can also drag and drop files onto the figshare add-on to upload a file. Uploading a file adds it to that
project on figshare as a draft.

If a new version of an already existent file is uploaded, two files with the exact same name will
appear in the add-on folder—they are not combined. Both these files will also appear in Figshare.

If a figshare file is selected by a user, a "View" button appears in the toolbar. Clicking this button or clicking the file title
brings the user to the details (rendering) page. Draft figshare files cannot be rendered. If the user clicks to render
a draft figshare file, in place of the rendered image is a blue alert::

    The file "[file name]" is still a draft on figshare.
    To view it on the OSF publish it on figshare.

No link is provided to view the file on figshare.

Public, published files on figshare are rendered on the OSF. Above the rendering is a link that reads::

    View this file on figshare.

Clicking this link sends the user to the figshare website.

When on the details page of a draft figshare file, no Download" button available. Users with editing permissions see a "Delete"
button on the details page of a draft file; clicking opens a confirmation modal::

    Delete file?
    Are you sure you want to delete [file name]?
    [Cancel][Delete]

Confirming the deletion brings the user to the file tree page where that file has been removed.

Public, published files cannot be deleted from the details page. A "Download" button is available.

If the user has editing privileges, clicking on a draft figshare file in the file tree shows a "Delete" button in the toolbar.
Clicking this button opens a modal::

    Delete "[file title]"?
    This action is irreversible.
    [Cancel][Delete]

If the user selects multiple draft files, a "Delete Multiple" button appears in the toolbar. Clicking opens a modal::

    Delete "[file title]"?
    This action is irreversible.

    [list of file titles]

    [Cancel][Delete]

After confirming, the files are removed from the OSF and figshare.

If the file is published, no "Delete" button is ever available from the file tree page. Two additional buttons
do show instead: "Download" and "View on figshare." Clicking "Download" will download a copy of the file.
Download counts are not available for figshare files. Clicking "View on figshare" will send the user to figshare
in that same browser window.

If multiple published files are selected, a "Download Multiple" button is available.

The user cannot select multiple published and draft files at once.

If the user attempts to move a draft file from figshare to OSF Storage, a red dismissable growlbox alert message will appear saying::

	Copy failed
	Cannot download private files.

The user receives an email as well::

    Hello,

    An error has occurred, and the file from [prject title] on The Open Science Framework was not successfully copied. Please
    log in and try this action again. If the problem persists, please email support@osf.io.

    The Open Science Framework Robot

Public, published figshare files can be copied to OSF storage. A copy of the file will be available in the figshare add-on and
the OSF Storage folders.

Files from other storage add-ons can be moved into figshare. These files are moved—not copied.

If the user moves a file with multiple versions into figshare, only the current version will be saved. All other versions will be lost.
Visiting the "revisions" view on a file's detail page shows a yellow alert in the revisions panel::

    figshare does not support file revisions.


Viewing GitHub Files
********************
**Purpose:** The file tree and file details pages allow users to view and interact with GitHub files.

GitHub appears in in the file tree as an item in the component to which it has been added. It is on the same level as OSF Storage.
The tree identifies the project::

    GitHub: [repo name] (branch)

File names from the indicated GitHub repo are shown in the file tree on the OSF.

Selecting the GitHub repo shows an "Open" button in the toolbar. Clicking sends the user to the GitHub website where the repo's
contents are shown.

A "Download as zip" button appears when a user selects the GitHub repo or any Github folder. Clicking **Download as zip** downloads the contents of the repo or folder as a zip file.

A "Create Folder" button is shown when the add-on is selected by a user with editing permission. The user types a
folder name and confirms creation. The folder is then shown inside the GitHub add-on. Files can be moved into and out
of the folder. If moving a file fails, a red growlbox alert appears::

    Move failed.
    Please refresh the page or contact support@cos.io if the problem persists.

Depending on the error, a different alert may appear::

    Move failed.
    Update is not a fast forward

Even if an error is shown, refreshing the page may show the file has been successfully moved.

Folders cannot be deleted.

If a file from a folder in GitHub is moved elsewhere or a new file is uploaded to a location in GitHub where a file
of the same name exists, a modal appears::

    Replace "[file name]"?
    An item named "[file name]" already exists in this location.
    [Cancel][Keep Both][Replace]

Choosing "Replace" creates a new version of the file. Choosing "Keep Both" adds an integer to the end of the moved file's title
to indicate the difference.

When a user with editing permissions selects GitHub in the file tree, an “Upload” button appears. Clicking on “Upload”
opens a modal that allows you to select files from within your computer to upload. Admins and read+write contributors
can also drag and drop files onto the GitHub add-on to upload a file. If a new version of an already existent file is
uploaded, the new version will replace the existing one.

Selecting the GitHub add-on also shows a "Branch:" dropdown. The dropdown lists all existing branches of the repo. It is visible
even if only one branch is available.

Selecting a file from the file tree shows a "Download" button in the toolbar.  No "Download Multiple" button
is ever available, even if multiple GitHub files are selected. Download counts are not available for GitHub.

If the user has editing privileges, clicking on a GitHub file in the file tree shows a "Delete" button in the toolbar.
Clicking this button opens a modal::

    Delete "[file title]"
    This action is irreversible.
    [Cancel][Delete]

After confirming, the file is removed from the OSF and GitHub.

Files from other storage add-ons cannot be moved into GitHub. Files from GitHub can be copied into other add-ons by dragging
and dropping, however.

Users with editing permissions can select a GitHub file to rename it. Clicking the "Rename" button that appears in the file
tree's toolbar opens a text box where the new name can be entered and saved.

If the connected repo is public, any user can select a file and see the "View on GitHub" button in the toolbar. Clicking
sends the user to the GitHub website where the file is displayed. If the repo is private, neither contributors nor visitors
see this button.

If a GitHub file is selected by a user, a "View" button appears in the toolbar. Clicking this button or clicking the file title
brings the user to the details (rendering) page where the file is rendered. No link is provided to view the file on GitHub. The file detail page will show the branch on the left hand file navigation bar. 

No actions can be performed if the user selects multiple files.

On the file's detail page, the image is rendered in the default "view" pane. Users with editing permissions see a "Delete"
button in the top right.

    Delete file?
    Are you sure you want to delete [file name]?
    [Cancel][Delete]

Confirming the deletion brings the user to the file tree page where that file has been removed.

A blue "Download" button is also available on the detail page. Clicking downloads the file.

Text and code files can be edited from the file detail page by users with edit permissions. Clicking "Edit" opens a pane
to the right of the rendered text where the user can revise the contents of the file. Saving updates the contents of the file.
No formatting options are available.

Selecting the "Revisions" button on the detail page opens the revisions pane. All commited versions of the file are listed.
The version ID, the date of the commit, and the user name of the editor is available. A download button is shown on the
right side of the pane.

All changes to GitHub via the OSF are logged as individual commits.

If a private repo is connected to a private project that is then made public, a warning appears in the confirmation modal
for making the project public::

    This component is connected to a private GitHub repository. Users (other than contributors) will not be able to see
    the contents of this repo unless it is made public on GitHub.

When the user confirms, contributors see a non-dismissable blue alert at the top of the page::

    Warning: This OSF component is public, but the GitHub repo [repo name] is private. Users can
    view the contents of this private GitHub repository through this public project.

If the GitHub repo connected is public, but the OSF project is private, a blue non-dismissable alert is visible at the top
of the page for all contributors::

    Warning: This OSF component is private, but the GitHub repo [repo name] is public. The files in this GitHub repo can
    be viewed on GitHub here.
    
    
GitLab
******
**Purpose**: The file tree and file details pages allow users to view and interact with GitLab files. The connection with GitLab is read-only.

GitLab appears in in the file tree as a storage provider. It is on the same level as OSF Storage::

    GitLab: [repo name] / (branch)

File names from the connected GitLab repo are shown in the file tree on the OSF.

Selecting the GitLab repo shows "Branch" menu, a "Download" button, and an "Open" button in the toolbar. The user can click inside the "Branch" menu
to select a branch from the repo. Clicking **Download** downloads the connected folder as a zip. Clicking **Open** opens the repo in GitLab.

The "Download" and "View" buttons appear when any user selects a GitLab file. Clicking **Download** downloads the contents of the repo as a zip file. Clicking **View** opens the file in the "File Details" page.
No link is provided to view the file on GitLab. 

Files from other storage add-ons cannot be moved into GitHub. Files from GitHub can be copied into other add-ons by dragging
and dropping, however.

If the project is public, but the connected repo is private, a blue banner appears at the top of the "File Details" page::
  
    Warning: This OSF project is public, but the GitLab repo beccarosenblatt / Data is private. Users can view the contents of this private GitLab repository through this public project.
  
On the "File Detail" page, the file is rendered in the default "view" pane. A blue "Download" and "View" button appears in the toolbar, along with a "Revisions" button. 
Clicking **Download** downloads the file. The "View" and "Revisions" buttons are toggled, where "View" is selected by default. Clicking **Revisions** highlights the
button in blue and the "View" button in white, and the revision history for the file replaces the rendered file. The date of the revision is available, and a "Download" button is shown on the right side of the pane.

If the project is public, a "Share" button will also be available in the toolbar. The "Share" tab provides a URL and a button to copy the URL to the user's clipboard. Below the URL field
are Twitter, Facebook, LinkedIn, and email buttons to share the URL on social media. The "Embed" tab provides two entries::
  
    Dynamically Render iFrame with JavaScript (with the associated javascript in a box below)
    
    Direct iFrame with Fixed Height and Width (with the assocated HTML in a box below)

If the GitLab repo connected is public, but the OSF project is private, a blue non-dismissable banner is visible at the top
of the page for all contributors::

    Warning: This OSF project is private, but the GitLab repo beccarosenblatt / Project_1 is public. The files in this GitLab
    repo can be viewed on GitLab here [links to the GitLab repo on GitLab].
    

    
    
    
    

Viewing Google Drive Files
**************************
**Purpose:** The file tree and file details pages allow users to view and interact with Google Drive files.

Google Drive appears in in the file tree as an item in the component to which it has been added. It is on the same level as OSF Storage.
The tree identifies the project::

    Google Drive: [folder name]

File names from the indicated Google Drive repo are shown in the file tree on the OSF.

A "Download as zip" button appears when any user selects the Google Drive add-on. Clicking downloads the contents of the folder as a zip file.

A "Create Folder" button is shown when the add-on is selected by a user with editing permission. The user types a
folder name and confirms creation. The folder is then shown inside the Google Drive add-on. Files can be moved into and out
of the folder. To delete a folder, users with editing permissions must select the folder and click on the "Delete Folder" button in the toolbar.
A modal opens::

    Delete "[folder]"?
    This folder and ALL its contents will be deleted. This action is irreversible.
    [Cancel][Delete]

When a user with editing permissions selects GitHub in the file tree, an “Upload” button appears. Clicking on “Upload”
opens a modal that allows you to select files from within your computer to upload. Admins and read+write contributors
can also drag and drop files onto the Google Drive add-on to upload a file. If a new version of an already existent file is
uploaded, the new version will replace the existing one.

Selecting a file from the file tree shows a "Download" button in the toolbar.  No "Download Multiple" button
is ever available, even if multiple Google Drive files are selected. Download counts are not available for Google Drive.

If the user has editing privileges, clicking on a Google Drive file in the file tree shows a "Delete" button in the toolbar.
Clicking this button opens a modal::

    Delete "[file title]"
    This action is irreversible.
    [Cancel][Delete]

If the user selects multiple files, a "Delete Multiple" button is shown in the toolbar. Clicking opens a confirmation modal::

    Delete "[file title]"?
    This action is irreversible.
    [list of file titles]
    [Cancel][Delete]

After confirming, the files are removed from the OSF and Google Drive.

Files from other storage add-ons can be dragged and dropped into Google Drive. Google Drive files can also be moved into other
add-ons, though the versions will not be kept (no warning is given).

Users with editing permissions can select a Google Drive file to rename it. Clicking the "Rename" button that appears in the file
tree's toolbar opens a text box where the new name can be entered and saved.

Any user can select a file and see the "View on Google Drive" button in the toolbar. Clicking
sends the user to the Google Drive website where the file is displayed.

If a Google Drive file is selected by a user, a "View" button appears in the toolbar. Clicking this button or clicking the file title
brings the user to the details (rendering) page where the file is rendered.

On the file's detail page, the file is rendered in the default "view" pane. Users with editing permissions see a "Delete"
button in the top right.

    Delete file?
    Are you sure you want to delete [file name]?
    [Cancel][Delete]

Confirming the deletion brings the user to the file tree page where that file has been removed.

A blue "Download" button is also available on the detail page. Clicking downloads the file.

Text and code files can be edited from the file detail page by users with edit permissions. Clicking "Edit" opens a pane
to the right of the rendered text where the user can revise the contents of the file. Saving updates the contents of the file.
No formatting options are available.

Selecting the "Revisions" button on the detail page opens the revisions pane. All saved versions of the file are listed.
The version ID and the date of the commit are available. A download button is shown on the right side of the pane.



Viewing Mendeley Content
************************
**Purpose:** Users can share their citations associated with a project using Mendeley.

From a project's :ref:`overview page <overview>`, Mendeley content can be viewed in a panel below the file tree. The panel is
titled "Mendeley."

At the top of the panel is a dropdown with placeholder text::
    Citation STyle (e.g."APA")

Below this are the citations that the user who connected the add-on has stored in the linked folder. Citations are listed in a table.
Below the "Citation" column is the citation for each resource, formatted according to the style selected in the dropdown.
In the "Actions" column there is a paper icon. Hovering over the icon shows a tooltip that reads "Copy Citation." Clicking the paper icon
copies the citation to the user's clipboard.

Users can change the citation style from the default APA by clicking in the dropdown and beginning to type a citation style. Suggestions
based on the input will appear as items in the dropdown. If the user selects one, the citations in the Citation column are
reformatted accordingly.

Viewing Zotero Content
**********************
**Purpose:** Users can share their citations associated with a project using Zotero.

From a project's :ref:`overview page <overview>`, Zotero content can be viewed in a panel below the file tree. The panel is
titled "Zotero."

At the top of the panel is a dropdown with placeholder text::
    Citation Style (e.g."APA")

Below this are the citations that the user who connected the add-on has stored in the linked folder. Citations are listed in a table.
Below the "Citation" column is the citation for each resource, formatted according to the style selected in the dropdown.
In the "Actions" column there is a "Copy to clipboard" button. Hovering over the button shows a tooltip that reads "Copy Citation." Clicking the button
copies the citation to the user's clipboard. The "Copy to clipboard" button is only supported on the file-level, and not the folder-level.

Users can change the citation style from the default APA by clicking in the dropdown and beginning to type a citation style. Suggestions
based on the input will appear as items in the dropdown. If the user selects one, the citations in the Citation column are
reformatted accordingly.

Viewing OSF Storage Files
*************************
**Purpose**: OSF Storage allows users to store and share files. 

Users can obtain and distribute links for their documents in public projects on the OSF so others can then view the same rendered files. In addition, users are provided two different methods of embedding those documents, one in which the iFrame is dynamically rendered and another which provides the iFrame directly.

If the user is an admin on the project, the following buttons are visible to them in the top right of the "File Details" page::

    Delete
    Share
    Download
    View
    Revisions

To any visitor viewing a file on a public project, only the "Share,""Download," "View," and "Revisions" buttons are visible in the top right of the "File Details" page.

When the user clicks the **Share** button, a popover appears with the following two tabs::
    
    [Share][Embed]

The "Share" tab provides a URL and a button to copy the URL to the user's clipboard. Below the URL field are Twitter, Facebook, LinkedIn, and email buttons to share the URL on social media.

The "Embed" tab provides two entries::
  
    Dynamically Render iFrame with JavaScript (with the associated javascript in a box below)
    
    Direct iFrame with Fixed Height and Width (with the assocated HTML in a box below)
    
When the user clicks the **Download** button, the file is downloaded onto their computer.

The user can toggle the "View" and "Revisions" buttons on and off. The selected button is blue and the unselected button is gray. The "View" button is automatically blue and selected for the user so that the file is displayed in the MFR when the user arrives on the "File Details" page. The "Revisions" button is automatically gray when the user arrives on the page.

When the user clicks the **Revisions** button, the "View" button turns gray and the "Revisions" button turns blue. Clicking the **Revisions** button shows a table of the different versions that the file has gone through (in the order of the most recent version to the oldest). The table format appears as follows::
  
    Version ID | Date | User | Download | MD5 [?]| SHA2 [?]

The "Version ID" column displays the version number (e.g. 1,2,3, etc.).

The "Date" column displays the date when the file version was created.

The "User" column displays the user's name which, when clicked, links to their profile page.

The "Download" column displays the number of times the file version has been downloaded.

The "MD5" column displays the MD5 algorithm and a button that the user can click to save the MD5 to their clipboard. The user can hover over the "?" to bring up a tooltip that explains MD5::
  
    MD5 is an algorithm used to verify data integrity.

The "SHA2" column displays the SHA2 algorithm and a button that the user can click to save the SHA2 to their clipboard. The user can hover over the "?" to bring up a tooltip that explains SHA2::
  
    SHA-2 is a cryptographic hash function designed by the NSA used to verify data integrity.

The user can click the most recent version ID to display the file in the MFR on the "File Details" page. When the user does this, the "View" button is selected and the "Revisions" button is grayed out in the top right of the page. Only the most recent file version can be displayed in the MFR.
