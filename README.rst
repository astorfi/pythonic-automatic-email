
**********************************************************
Sending Multiple Customized Emails Uing Gmail API & Python 
**********************************************************

This repository is dedicated to show how to use `Python Gmail API`_.

.. image:: https://github.com/astorfi/Send-Multiple-Emails/blob/master/_img/source.gif
      

.. _Python Gmail API: https://developers.google.com/gmail/api/quickstart/python

==========
Motivation 
==========

There are couple of questions as motivate someone to use the python API for sending customized gmail.

    * What if you one to send a fixed email to multiple people at once?
    * What if you one to send multiple emails to a certain individual at once?
    * What if you want to send multiple emails to multiple people?
    * What if you want to almost similar emails to multiple people with only changing the subject or greeting customized by their first name?
    
Consider the aformentioned variations, using an API to easily change the email format and content using a ``predefined pattern`` or a ``parsed text`` is of great interest. As an example, let's consider we have a ``.csv`` file which has multiple subjects with their information. Suppose we want to parse the ``.csv`` file and send an invitation email to each individual when only the initial part of the emails is different which is ``Dear X or Dear Y`` for example. Using a python interface can make life easy and come to rescue us. In this repository, the exact aforementioned example will be addressed.

==============
Bigger picture
==============

At first time the python script opens a browser to take and store ``Gmail credentials`` locally. Then by using another script, the message creation will be performed. *We basically use the codes provided by google* except we customize few things to parse the ``.csv`` file and write the email format.

=================================================
Run the Gmail API, Installation and authorization
=================================================

At first, the ``Gmail API`` must be initialized. Please refer to `this link <PythonQuickstartGmailAPI_>`_. After turning on the Gmail API, the ``Google Client Library`` must be installed by executing the following in the command line:

.. code:: shell 
     
     pip install --upgrade google-api-python-client
     

After installation, the file ``code/quicksetup.py`` must be run for providing the credentials locally. Remember the file ``client_secret.json`` must be provided and it could be downloaded when the Gmail API is being turned.

.. _PythonQuickstartGmailAPI: https://developers.google.com/gmail/api/quickstart/python

=====================
Send customized email
=====================

Now the interface is ready to go. Let's take a look and our main file ``code/sendmessage.py``. It is the code `at here <code_>`_ with some minor changes. We parse the ``.csv`` file and send customized emails.

.. _code: http://stackoverflow.com/questions/37201250/sending-email-via-gmail-python

Take a look at the context of the ``sample .csv file``:

.. code:: shell 
     
     FirstName,LastName,EmailAddress,Company,Position
     subject_name,subject_lastname,subject_email,X Corporation,Sr. Deep Learning,
     
The ``.csv`` file can contain multiple lines of different individuals of information. We parse it as follows:

.. code:: python

      def sendmail(attribute):
          first_name = attribute[0]
          last_name = attribute[1]
          email = attribute[2]
          print('Sending email to %s' % (str(email)))

          to = email
          sender = "you.email@gmail.com"
          subject = "subject"
          msgPlain = ""
          msgHtml = "Hi "+ first_name +",<br/>This is a test email"
          SendMessage(sender, to, subject, msgHtml, msgPlain)


       def main():
         with open("file.csv", "rb") as csvfile:
              msg_reader = csv.reader(csvfile)
              msg_reader.next()
              map(lambda x: sendmail(x), msg_reader)

So for each individual email, we just change the name and sent it again. That's all. Seems super easy but the problem is easy when it is solved, right?


==========
Final Note
==========

Before using this codes, first just provide a simple ``.csv`` file or whatever file you want to parse, and use only your emails to make sure nothing is messed up. because the last thing you want is to send wrong emails to multiple people.


