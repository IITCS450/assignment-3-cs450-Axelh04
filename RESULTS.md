# RESULTS

Axel Hernandez
CS450 ASSI 3

## MY SETUP

Only ran with CPUS=1

3 child processes -> child A gets 1 ticket, child B gets 2 tickets, child C gets 3 tickets, so 6 tickets total, and shares are like 1/6, 2/6, 3/6.

## TEST QUALITY

AxelsNewTest.c selects three kids, and each one uses the ticket amount to call settickets(). Then, using uptime() to measure time, each kid completes a 500-tick CPU-bound work loop. Each one prints the number of work units completed at the end. The child who has more tickets is scheduled more often and completes more tasks at once.

## OUTPUT

when ran:
child tickets=1 work=3469
child tickets=2 work=5896
child tickets=3 work=8021

if you divide everything by the smallest (3469):
- 1 ticket: 1.0x
- 2 tickets: 1.70x
- 3 tickets: 2.31x

Although it is not exact, it is rather near to the 1x, 2x, and 3x expected. There is no denying the trend: more tickets equal more CPU time. There is usually some fluctuation because the scheduler employs random integers, and because there are fewer scheduling decisions for short trips, the noise is more noticeable. The rng is also straightforward deterministic lcg that distributes rather well across longer draws since its more.
