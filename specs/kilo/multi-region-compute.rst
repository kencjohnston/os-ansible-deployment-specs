Multi Region Compute
#################################
:date: 2015-06-15 01:00
:tags: multi-region, scalability

This spec is to propose adding support for multi-region clouds in OSAD.

Launchpad blueprint: N/A

Deployers who are interested in OpenStack clouds are often interested in
private clouds specifically for security, performance and reliability reasons.
At present they have no way to ensure reliability in the event of an entire
data center being down without having entirely separate geographically
redundant clouds. An improved experience is to be able to manage and
authenticate across individual clouds through the concept of multiple-regions.
This process and experience is already largely defined by existing public
clouds and a customers initial frame of reference is going to be to compare to
a multi-region/multi-geography public cloud.

Problem description
===================

* As a user, in order to ensure ease of authentication within my multi-region
  cloud, I should be able to use my common credentials to authenticate with
  any regional Keystone

* As a user, in order to ensure a complete understanding of available
  services, I should be able to query a Keystone service catalog in any region
  and receive a response with service endpoints for all regions

* As a user, in order to have a seamless dashboard experience, I should be
  able to login with any credentials to any dashboard and toggle between
  regions to see each region and services available without supplying
  credentials again

* As an administrator, in order to successfully control access to services and
  regions, I should be able to limit users and tenants to services in specific
  regions

* As a cloud deployer, in order to seamlessly deploy a multi-region cloud, I
  should be able to use playbooks to deploy the multi-region cloud additively
  including service configuration, container deployment and inter-cloud
  networking deployment

* As a cloud deployer, in order to ensure business continuity in a transition
  from single to multi-region, I should have my service deployed in such a way
  as to minimize the potential impact of a transition

* As a user, in order to meet my existing expectations from my usage of public
  clouds, I should experience some services as global (Identity, Dashboard)
  and other services as regional (Compute, Networking, Image, Block Storage,
  Orchestration)


Proposed change
===============

The two services to be experienced as global are Identity and Dashboard.
Proposing the Identity service be synchronized between multiple clouds so that
domains/projects/users are available in all regions. Proposing Dashboard be
configured to present multiple regions through a single interface.


Alternatives
------------

Could be accomplished via Identity Federation which lacks HA and has a
different authentication mechanics.


Playbook impact
---------------
N/A



Upgrade impact
--------------
N/A


Security impact
---------------
N/A


Performance impact
------------------
N/A


End user impact
---------------
N/A


Deployer impact
---------------
N/A


Developer impact
----------------
N/A


Dependencies
------------
N/A


Implementation
==============

Assignee(s)
-----------

Who is leading the writing of the code? Or is this a blueprint where you're
throwing it out there to see who picks it up?

If more than one person is working on the implementation, please designate the
primary author and contact.

Primary assignee:
  <launchpad-id or None>

Other contributors:
  <launchpad-id or None>

Please add **IRC nicknames** where applicable.

Work items
----------

Work items or tasks -- break the feature up into the things that need to be
done to implement it. Those parts might end up being done by different people,
but we're mostly trying to understand the timeline for implementation.


Testing
=======

Please discuss how the change will be tested. You should be able to answer the
following questions:

* Does this change impact how gating is done?

* Can this change be tested on a **per-commit** basis?

* Given the instance size restrictions, as found in OpenStack Infra
  (8GB Ram, vCPUs <= 8), can the test be run in a resource constrained
  environment?

* Is this untestable given current limitations (specific hardware /
  software configurations available)? If so, are there mitigation plans
  for this change to be tested within 3rd party testing, gate enhancements,
  etc...?

* If the service is not OpenStack specific how can we test the change?


Documentation impact
====================

What is the impact on the docs team of this change? Some changes might require
donating resources to the docs team to have the documentation updated. Don't
repeat details discussed above, but please reference them here.


References
==========

Please add any useful references here. You are not required to have any
reference. Moreover, this specification should still make sense when your
references are unavailable. Examples of what you could include are:

* Links to mailing list or IRC discussions

* Links to relevant research, if appropriate

* Related specifications as appropriate

* Anything else you feel it is worthwhile to refer to
