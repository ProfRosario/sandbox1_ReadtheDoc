Usage
=====

.. _installation:

Installation
------------

To use Lumache, first install it using pip:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']


This a test
-----------

How to Generate Private and Public SSH Key
-----------------------------------------

To create private and public SSH keys, type the following command:

.. code-block:: console

   $ ssh-keygen -t rsa

This command tells ssh to generate a rsa type key. The following message will display:

.. code-block:: console
   
   Generating public/private rsa key pair.
   Enter file in which to save the key (/c/users/username/.ssh/id_rsa):


If the file path is correct, do not type any informatin just press Enter. The following message will appear:

.. code-block:: console

   users/username/.ssh/id_rsa already exists.
   Overwrite (y/n)

If you want to delete the old key, type y and press Enter. Otherwise type n. 

The following message will appear if you typed y:

.. code-block:: console
   Enter passphrase (empty for no passphrase)

Type a passphrase that you can remember (not too complicated) and press Enter. The following message will appear:

.. code-block:: console

   Enter same passphrase again:

Retype the passphrase again and press Enter. The following messages will appear:

.. code-block:: console

   Your identification has been saved in id_rsa.
   Your public Key has been saved in id_rsa.pub.
   The key finger print is:
   f3:15:57:.....................:db username@domain.com

Try to remember the finger print image (appearance). You don't need to memorize the actual message.
Note, two keys will be generated, a public key and a private key. The private key should be stored on your main computer and the public key (with the .pub extension) should be stored at the remote host (example: raspberry pi, github,...,etc). 

How to change the passphrase.
-----------------------------
If you made a mistake or don't like your old passphrase, you can change it without changing the private and public keys. Type the following command:

.. code-block:: console

   $ ssh-keygen -p </code>  

-p is requesting to change the passphrase only. Don't worry this doesn't change the key.


Start the SSH Agent
--------------------

Type the following commands:

.. code-block:: console
   $ ssh-agent $SHELL
   $ ssh-add

The following message will appear:

.. code-block:: console

Enter passphrase for /home/you/.ssh/id_rsa:
Identify added: /home/you/.ssh/id_rsa

Setup the Raspberry Pi
----------------------------

Copy your public ssh key to your  ~/.ssh folder. In the .ssh folder, you should see a text file named authorized_keys. If you don't see it, type the following command

.. code-block:: console

   $ touch authorized_keys</code>

"touch" is a Linux command that creates a blank text file with nothing inside.

Next type the following command to append the public key to your authorized_keys file on the Pi, sending it over SSH:

.. code-block:: console

   $ cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'cat >> .ssh/authorized_keys

If you typed everything correctly, next time you run the ssh-agent you will not have to authenticate with your password again.

Transfering files without username or password
-----------------------------------

.. code-block:: console

   $ git clone git@github.com:github_username/MyRepro.git

If you set everything correctly, Github should not asking you for your username or password any more when cloning. If GitHub does, you probability made a mistake somewhere in the setup.



