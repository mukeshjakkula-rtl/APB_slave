# APB_slave
### apb_states - IDLE, SETUP, ACCESS
added buffers for the pwrite,paddr,pdata so that if master changes the these signals when it sees the pready is high to avoid the race condition for slave to capture the data.

in setup state we wait for penable to go to the access state and 
in access state we see if penable is high we latch the datas so this 

in sepc it is mentioned that untill pready is high
pdata,paddr,psel,pwrite,penable have
to be stable but in access state after pready is high the next triggering
edge only the transaction capturing happens so what if the data changes
immediately after access state cause the state changes immediatly when
pready is high 

so all these things have to happen at the same triggering edge after pready going high 
state change from access to idle
capturing the data from master or giving data to master 
master chnaging the signals according to next transactions 
so to avoid the race conditions we use internal buffers 



// still we have buffers to get reliable data 
// could cause issues if paddr,pwdata,pwrite changes immediately in access
// state so, // we add buffers for all those signals in setup state

