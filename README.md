# Chargebee status/pop-up Document

# Fields

  payment_status
  
  subscription_phase
  
  status
  

# Field value holders

  payment_status - [paid, due, null]
  
  subscription_phase - [active, in-trial, ready to subscribe]
  
  status - [active, not paid, subscription created, subscription created not paid, yet to create]
  

---

# Conditions on pop-ups
 - # active
subscription_phase = 'active' | status = 'active' | payment_status = null  ==> no pop-up

subscription_phase = 'active' | status = 'active' | payment_status = 'paid'  ==> no pop-up

subscription_phase = 'active' | status = 'active' | payment_status = 'due'  ==> hard pop-up
<img width="500" alt="image" src="https://github.com/user-attachments/assets/aa0f7594-e1a5-4c5b-aa29-c00b58364257">

---

subscription_phase = 'in-trial' | status = 'subscription created' | payment_status = null  ==> no pop-up

subscription_phase = 'in-trial' | status = 'subscription created' | payment_status = 'paid'  ==> no pop-up

subscription_phase = 'in-trial' | status = 'subscription created' | payment_status = 'due'  ==> hard pop-up
<img width="500" alt="image" src="https://github.com/user-attachments/assets/aa0f7594-e1a5-4c5b-aa29-c00b58364257">

[ps : the current logic neither sets the paymet_status not updates the status for **IN-TRIAL SUBSCRIPTION CREATED CLIENTS**]


subscription_phase = 'in-trial' | status = 'subscription created not paid' | payment_status = null or 'paid' or 'due'  ==> hard pop-up
<img width="500" alt="image" src="https://github.com/user-attachments/assets/aa0f7594-e1a5-4c5b-aa29-c00b58364257">


subscription_phase = 'in-trial' | status = 'yet to create' | payment_status = null or 'paid' or 'due'  ==> free-trial/create account pop-up
<img width="397" alt="image" src="https://github.com/user-attachments/assets/0e7aaa26-0e85-46d5-b2e4-66676aadd1c5">

---
[for subscription_phase = 'ready to subscribe' and status = 'active' additional field named schedule_clicked is also checked]

subscription_phase = 'ready to subscribe' | status = 'active' | payment_status = null  ==> no pop-up

subscription_phase = 'ready to subscribe' | status = 'active' | payment_status = 'paid' | schedule_clicked = true ==> no pop-up

subscription_phase = 'ready to subscribe' | status = 'active' | payment_status = 'paid' | schedule_clicked = false ==> pt schedule pop-up
<img width="397" alt="image" src="https://github.com/user-attachments/assets/799e496b-404e-4fa0-8f16-c9672945ad31">


subscription_phase = 'ready to subscribe' | status = 'active' | payment_status = 'due' | schedule_clicked = true   ==> hard pop-up
<img width="500" alt="image" src="https://github.com/user-attachments/assets/aa0f7594-e1a5-4c5b-aa29-c00b58364257">


subscription_phase = 'ready to subscribe' | status = 'active' | payment_status = 'due' | schedule_clicked = false   ==> pt schedule pop-up
<img width="397" alt="image" src="https://github.com/user-attachments/assets/799e496b-404e-4fa0-8f16-c9672945ad31">


subscription_phase = 'ready to subscribe' | status = 'not paid' | payment_status = null or "paid" or "due"   ==> create account pop-up
<img width="397" alt="image" src="https://github.com/user-attachments/assets/3f2e690d-337f-4699-b137-68c50d949fa3">



