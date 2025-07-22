The Sliding Window Paradigm now uses [[ARQ]], Receiver- and Congestion Window Size to ensure all presented conditions are met. As defined, we have:

• sender window size (swnd) : Defines how many packets are sent concurrently
• receiver window size (rwnd) : Defines how many packets are accepted by the receiver
• congestion window size (cwnd) : Is given by the capacity of the network.

# sender output
Then the main idea is to make the sender output dependent on the two metrics we have defined beforee:
$$min(cwnd, rwnd) $$
# Head of line blocking
Generally refers to a problem that happens when the first item in a line (or queue) is held up, and it stops everything behind it from moving forward — even if those things could otherwise go through.
*In networking:* a problem which occurs when a protocol uses the sliding window approach.

>Head of Line blocking describes the effect that packets have to wait for a previous packet to be acknowledged in order to be received.

This can be partially prevented by introducing **buffers** but not fully as buffer sizes are limited (and thus finite).