According to a security model, any system or piece of technology storing information is called an information system, which is how we will reference systems and devices.

Some popular and effective security models are:

### The Bell-La Padula Model
This model is used to achieve confidentiality. It has a few assumptions, an organization's hierarchical structure that it is used in, where everyone's roles and responsibilities are well-defined.

The model works by granting access to objects (data) on a strictly need to know basis. The Bell-La Padula Model uses the rule "no write down, no read up".

Some advantages and disadvantages of this model are:

| **Advantages**                                                                                   | **Disadvantages**                                                                                                                  |
| ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| Policies in this model can be replicated to real-life organizations hierarchies (and vice versa) | Even though a user may not have access to an object, they will know about it's existence. So it's not confidential in this aspect. |
| Simple to implement and understand, and has a proven track record of success.                    | The model relies on a large amount of trust within the organization.                                                               |
|                                                                                                  |                                                                                                                                    |
![[Pasted image 20240715140144.png]]
 The Bell LaPadula model is popular in government and military organizations because members are presumed to have already gone through a vetting process. This is the process where applicants are screened to establish the risk they pose to the organization.
### Biba Model

The Biba model is arguably the equivalent of the Bell-La Padula model but for the integrity of the [[CIA Triad]]. 

This model applies the rule to objects and subjects (users) that can be summarized as "no write up, no read down". This means that subjects **can** create or write content to objects at or below their level, but **can only** read the contents above the subject's level.

A couple advantages and disadvantages of the Biba model are:


| **Advantages**                                                                                              | **Disadvantages**                                                                                                                                   |
| ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| This model is simple to implement                                                                           | There will be many levels of access and objects, increasing the chance that things can be overlooked when applying security controls.               |
| Resolves the limitations of the Bell-La Padula model by addressing both confidentiality and data integrity. | Often results in delays within a business. For example, a doctor would not be able to read the notes made by a nurse in a hospital with this model. |
![[Pasted image 20240715141021.png]]
The Biba model is used in orgs or situations where integrity is more important than confidentiality. For example, in software development, developers may only have access to code that is necessary for their job. They may not need access to critical pieces of information such as databases, etc.