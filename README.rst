
##################################
Sending Multiple Customized Emails
##################################

This repository is dedicated to show how to use `Python Gmail API`_.

.. _Python Gmail API: https://developers.google.com/gmail/api/quickstart/python

***********
Motivation 
***********

There are couple of questions as motivate someone to use the python API for sending customized gmail.

    * What if you one to send a fixed email to multiple people at once?
    * What if you one to send multiple emails to a certain individual at once?
    * What if you want to send multiple emails to multiple people?
    * What if you want to almost similar emails to multiple people with only changing the subject or greeting customized by their first name?
    
Consider the aformentioned variations, using an API to easily change the email format and content using a ``predefined pattern`` or a ``parsed text`` is of great interest. As an example, let's consider we have a ``.csv`` file which has multiple subjects with their information. Suppose we want to parse the ``.csv`` file and send an invitation email to each individual when only the initial part of the emails is different which is ``Dear X or Dear Y`` for example. Using a python interface can make life easy and come to rescue us. In this repository, the exact aforementioned example will be addressed.
