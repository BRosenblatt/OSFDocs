**Purpose:** The registries search is an OSF search, linked to from the "OSF Home" tab, that allows the user to browse all public registrations on the OSF, including withdrawn registrations.

This page is accessible at https://osf.io/registries.

Links included when logged out
==============================

* OSF Registries
    
    * OSF Home: Clicking this link takes the user to their dashboard. 
    * OSF Preprints: Clicking this link takes the user to the OSF Preprints landing page https://osf.io/preprints/.
    * OSF Registries: Clicking this link takes the user to the OSF Registries landing page https://osf.io/registries/.
    * OSF Meetings: Clicking this link takes the user to the OSF for Meetings landing page https://osf.io/meetings/.

* Search: Clicking this tab takes the user to the OSF Registraties "Discover" page https://osf.io/preprints/discover/.

* Support: Clicking this tab takes the user to the OSF Registrations support landing page: http://help.osf.io/m/registrations/

* Sign Up: Clicking this tab takes the user to the :ref:`Create a free account page <sign-up>` where the user needs to fill out a form to create an OSF account.

* Sign In: Clicking this tab takes the user to the :ref:`OSF sign-in page <login>`. After logging in, the user is taken to the OSF Registraties landing page.

Links included when logged in
=============================

When logged in, the navigation bar is the same, except that the "Sign Up" and "Sign In" links are replaced with the user drop-down menu:

* Username
     
    *My Profile: Clicking this link takes the user to their profile page https://osf.io/profile/.
    *OSF Support: Clicking this link takes the user to the support page https://osf.io/support/.
    *Settings: Clicking this link takes users to their user settings page https://osf.io/settings/.
    *Log out: Clicking this link logs the user out of their OSF account and takes them to the OSF homepage, where a confirmation message will appear at the top of the page informing them that they have logged out succesfully: https://osf.io/goodbye/. 

Searching OSF Registries
========================
OSF Registries is powered by SHARE. On the OSF Registries landing page, the user can search for registrations by typing a query into the search box or by clicking a registration in the "Browse Recent Registrations section."

When the user clicks a registration below the "Browse Recent Registrations section," they are taken to the registration form for that registration. 

When the user types a query into the search box on the landing page, search results relevant to that query will appear.

To search by registration titles, the user can simply enter the title into the search box and press **enter** on their keyboard or click the **search** button. To search by author(s) or keyword(s), the user should use the boolean operators *AND* and *OR*. To refine a search with boolean operators, the user should type any of the following syntaxes:

**SEARCH BY AUTHOR**
* author:(albert einstein)

* author: “albert einstein”

* author: ‘albert einstein’

* authors:(nosek AND spies)

* authors: “nosek AND spies”

* authors:’nosek AND spies’

**SEARCH BY KEYWORD**

* tags:”multimedia”

* tags:(multimedia)

* tags: ‘multimedia’

* tags:”computer AND science”

* tags:(computer AND science)

* tags:’computer AND science’

* tags:”psychology OR neuroscience”

* tags:(psychology OR neuroscience)

* tags:’psychology OR neuroscience’

On the OSF Registries search page, there are two left sidebars with filters by which the user can refine their search:

* a "Provider" sidebar that shows all of the registration providers that OSF Registries aggregates
* an "OSF Registration Type" sidebar that shows all of the registration types that the OSF offers. 

The user can select a registration provider to search for registrations posted to a specific provider.

The "OSF Registration Type" sidebar will only be available to the user if they select **OSF Registries** and only **OSF Registries** from the "Provider" sidebar. Otherwise, the "OSF Registration Type" sidebar will be grayed out and will have a red alert above it that reads::
  
    Only available with OSF Registries

If the user selects **OSF Registries** and any additional providers, the "OSF Registration Type" sidebar will be unavailable to use. 

When the user selects **OSF Registries**, the red alert disappears and the sidebar becomes available. The user can check the boxes next to the registration types by which they want to filter search results. Checking the boxes will show the public registrations that are of those registration types.

Registration search results display the registration title first, followed by the author(s), description, provider, date the project was registered, links, and the date on which the registration was added.

