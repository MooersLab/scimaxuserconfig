# Blaine's user.el configuration file for scimax


This repo has my user.el file for scimax.
SciMax is a highly customized Emacs profile for scientists.
It was happen developed by John Kitchin at the Carniege Mello University. 

I am using scimax to learn about the features that are wanting in my own configurations.
For example, I using it to learn about org-ref.
Yes, using someone else's configuration feels like sleeping in someone else's bed!
I do not intend to migrate to scimax: I am just visting on a sabbattical from my vanilla GNU Emacs configuration.
However, these additions are making scimax more comfortable.
I need to stay long enough to read the manual.

The **user.el** file is the user's configuration file for scimax.
It resides in the *user* subfolder of the *scimax* folder.
The  **user.el** file contains the Emacs keybinding and packages that I cannot live without.
For example, it contains the keybindings that map the Mac option key to the super key and the  right-option key on the hyper key.
It also contains the keybinding of s-<right> to next buffer and s-<left> to the previous buffer.
These are very convenient for moving from the org file  in the current buffer and to the bib file in the next buffer and back again without using the mouse.
I have included my minibuffer history keybindings and the configuration for bibtex and org-ref.

## Features:

- Hyper, super, meta keybindings
- Next and previous buffer keybindings
- Settings for paths to global.bib file and the folders for storing PDFs.
- Minibuffer history keybindings
- Command to load scimax.org into a buffer (this is the manual for scimax).
- Command to load user.el into a buffer to ease the addition of more configuration. (This is redundant with the option *Customize user.el* under the *Scimax* pulldown).
- Gray highlight of current line
- Move the current line or region up or down with the meta key and the arrow keys.
- Configuration for org-agenda
- tex-count for LaTeX files
- 


Packages can be installed with use-package.
For example, execute (use-package atomic-chrome) in the user.el file to install atomic chrome.

## Packages added:

- atomic chrome to run ghosttext (yes it works!)
- get-bibtex-from-doi
- org-drill
- org-pomodoro
- org-roam
- wc-mode

## How I invoke scimax

I git cloned scimax to my home directory.
I mapped the alias *eis* to Emacs running the scimax configuration by adding the following line to my zshrc file:

```bash
eis='/Applications/Emacs29.0.5.app/Contents/MacOS/Emacs --init-directory ~/scimax'
alias eis
```
Please note that I am using the *--init-directory* flag that is only available for Emacs version 29.

## Fetching bibtex entries

I started using scimax to enter BibTeX  entries into my global.bib file.
I reasoned that scimax might have better support for org-ref than the configurations that I had built in my default configuration and my *latex-emacs* configuration.
For the last two, I am able to fetch BibTeX entries using DOIs, but I am not able to have the automated downloading and labeling of the corresponding PDFs that attracted me to org-ref.

I am still not able to get the automated download of PDFs to happen, but the fetching of BibTeX entries runs more smoothly in scimax.
I may need to dig into the *doi-utils* package.
My keybinding to the function *doi-add-bibtex-entry* is not working, but this function it at the top of the list when I enter M-x, even after logging out and re-entering scimax.
I need to figure out what is causing this feature and then add it my other configurations.
My protocol is as follows:

- Open a manuscirpt.org file.
- Scroll down to the bibliography key.
- Click on the global.bib file to open it in a new buffer.
- Move to that buffer with the s-<right> keybinding.
- Move the point to the bottom of global.bib.
- Copy the DOI to the clipboard.
- Enter M-x and select doi-add-bibtex-entry and then hit return.
- A DOI field will appear with the stored DOI automatically entered. 
- Hit return to have the BibTeX entry inserted at the point.
- Move the point inside the bibtex entry and enter *exciting<tab>* to insert four missing fields that are partly filled out.
- Fill in the missing fields.
- Save global.bib from Emacs.
- Load global.bib into JabRef.
- Generate the bibtex citekey.
- Copy the citekey over the filename prefix of the PDF.
- Add the keywords to the PDF with the tags program.

A time stamp is included in the BibTeX entry.
This time stamp can narrow the search for the most recently entered entries using Emacs or JabRef.
JabRef can send a selected entry to a latex or org-mode buffer in Emacs as a citekey if JabRef has been configured to use Emacs as its default external editor under Option/Preferences.

Note that *exciting* in the list above a tab-trigger for a snippet that I stored in the bibtex-mode folder that I created in the snippets folder. 
It has the keywords for the *exciting* cluster of projects.
These keywords ease retrieval of the bibtex entries in JabRef.

I have add the keywords as tags to the PDFs by using the tags program.
These are meant to aid in the selection of PDFs with the finder in the Mac.
