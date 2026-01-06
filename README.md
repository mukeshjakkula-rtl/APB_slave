# APB_slave
### apb_states - IDLE, SETUP, ACCESS
added buffers for the pwrite,paddr,pdata so that if master changses the these signals when it sees the pready is high to avoid the race condition for slave to capture the data.
