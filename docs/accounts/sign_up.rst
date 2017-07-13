.. _todo: update from 0.47—new flow on login for the first time.

**Purpose:** The sign-up form creates an OSF account.

The sign-up form can be accessed only while logged out, from the OSF homepage (osf.io). This form requests the user’s full name, contact email, confirmation of their contact email, and a password.

Below these fields is a CAPTCHA section (run by reCAPTCHA) to ensure that the user setting up an account is not spam::
  
  [checkbox] I'm not a robot

After the user checks the box to confirm that they are not a robot, a green check mark will appear in place of the check box. The user cannot undue this section.

If the user fills out all of the fields correctly and checks the box but then lets the page sit for several minutes (about five minutes) without submitting their form, reCAPTCHA will expire and the user will need to re-check the checkbox. The checkbox will be outlined in red and the following red error message will appear above it::
  
    Verification expired. Check the checkbox again.

If the user clicks **Create account** without checking the box, a red error messaage will appear that reads::
  
    Please complete reCAPTCHA

After successfully submitting, the user cannot click into any of the fields.

If the user does not complete a field, but clicks into a subsequent field or returns to a previous field or submits the form, an alert below the field(s) reads::

    This field is required.

If the user enters a name that has fewer than three characters, but clicks into a subsequent field or submits the form, an alert written in red below the name field reads::

    Please enter at least 3 characters.

If the user enters no email address, but clicks into another field or submits the form, an alert below the field reads::

    This field is required.

If the user does not enter a complete email address, but clicks into another field, an alert written in red below the email field reads::

    Please enter a proper email address.

If the user enters two different email addresses and clicks into another field, an alert written in red below the field reads::

    Emails must match.

If the user does not enter a password that has at least 6 characters, but clicks into another field, an alert written in red below the email field reads::

    Please enter at least 6 characters.

If the user enters a password that is longer than 256 characters, but submits the form, an alert written in red below the email field reads::

    Please enter at least 6 characters.

Clicking “Sign up free” while any error alert is still showing produces no result.


If the user tries to sign-up with an unregistered email, an inline success alert is shown on the page. The user is told::

    Registration successful. Please check [email] to confirm your email address.


If the user tries to sign-up with a registered but unconfirmed email, an inline success alert is shown on the page. The user is told::

    Registration successful. Please check [email] to confirm your email address.

The user receives an email::

    Hello [User Name],
    Please confirm your email address by visiting this link:
    URL
    From the Open Science Framework Robot

If the user tries to sign-up with an email that had been listed as an" :doc:`alternate </account_settings>` but that was removed, an inline success alert is shown on the page. The user is told::

    Registration successful. Please check [email] to confirm your email address.

The user receives an email::

    Hello [User Name],
    Please confirm your email address by visiting this link:
    URL
    From the Open Science Framework Robot

If the user tries to sign-up with a registered email, an inline red alert is shown on the page. The user is told::

    The email [email] has already been registered

No email is sent.

If the user tries to sign-up with a :doc:`deactivated </account_settings>` account's email, an inline red alert is shown on the page. The user is told::

    The email [email] has already been registered

No email is sent.

Confirming an Unregistered User Account
---------------

**Purpose:** Users can be added as contributors to an OSF :doc:`project <../projects/project_index>` without having an account. In this case can claim an account so that they may access the material.


Claiming an Account Via Email
^^^^^^^^^^^^^^^^
**Purpose:** Claiming an account via email allows a user who has been added as a contributor to a project to create an account following their addition.

If a user is added as a contributor to a project, but does not have an OSF account, they will receive an email in their inbox instructing them that they can set a password for their account::

    Hello [Name of account being claimed],
    You have been added by  [User who added unclaimed account as contributor] as a contributor to the project "[Project Name]" on the Open Science Framework. To set a password for your account, visit:
    URL
    Once you have set a password, you will be able to make contributions to [Project Name].
    Sincerely,
    The OSF Team
    If you are not [Name of account being claimed] or you are erroneously being associated with [Project Name] then email contact@osf.io with the subject line "Claiming Error" to report the problem.

If the user has confirmed their account and is signed into the OSF, but follows the email’s link again, they are brought to a page that informs them they are already a contributor.

If the user has confirmed their account and is not signed into the OSF, but follows the email’s link again, they are brought to a page that informs them that the account has already been claimed.

.. todo:: what if they do it right?

Claiming an Account Via the OSF
^^^^^^^^^^
**Purpose:** Claiming an account via the OSF allows a person who does not have an OSF account to identify themselves as a contributor on a project.

If a user finds their name listed on an OSF project but does not have an OSF account, they can claim their account. To do so, the user clicks on their name in contributor list. This name is not linked to a :doc:`public profile <../profiles/profiles_index>`. Hovering over their name shows a tooltip that says “Is this you?  Click to claim.” After clicking, a popover appears. The popover is titled “Claim account” and a blank text field instructs the user to enter their email. The user enters their email into the field and clicks the check mark to the right. Alternatively, the user can click the ‘x’ to the right of the check mark to cancel.

After submitting, a dismissable success growl-box alert appears in the upper right corner of the page. It reads “Email will arrive shortly. Please check [email].” An email is sent automatically to the entered address. The email does not allow them to sign into the account, but instead informs them that their request to claim the account has been received::

    Hello [Name of account being claimed],
    We received your request to claim an OSF account and become a contributor for "[Project name]".
    To confirm your identity, has been sent an email to forward to you with your confirmation link.
    This link will allow you to complete your registration.
    Thank you for your patience.
    Sincerely,
    The OSF Team

The user who added the unclaimed account as a contributor is also sent an email. This email asks the user to forward the message to the correct person::

    Hello [User who added unclaimed account as contributor],
    You recently added [Name of account being claimed] to "[Project Name]". [Name of account being claimed] wants to claim their account, but the email address they provided is different from the one you provided.  To maintain security of your project, we are sending the account confirmation to you first.
    IMPORTANT: To ensure that the correct person is added to your project please forward the message below to [Name of account being claimed].
    After [Name of account being claimed] confirms their account, they will be able to contribute to the project.
    ----------------------
    Hello [Name of account being claimed],
    You have been added by  [User who added unclaimed account as contributor] as a contributor to the project "[Project Name]" on the Open Science Framework. To set a password for your account, visit:
    URL
    Once you have set a password, you will be able to make contributions to [Project Name].
    Sincerely,
    The OSF Team

 After being forwarded the email, the user claiming the account is sent to a “Set Password” page. This page asks the user to “set a password to claim your account.” The email they are registering with is shown, but not editable. The user is asked to create a password and confirm it. There is a note that reads::

    If you are not [User name], or if you were erroneously added as a contributor to the project described in the email invitation, please email contact@osf.io.

The user can save their input and is then brought to their :ref:`profile information <profiles>` page.

