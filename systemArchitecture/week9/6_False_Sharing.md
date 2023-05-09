> This is in week 10 video 1 but relates to week 9
# False Sharing
* Can occur in either #snoopingCoherencyProtocol or #directoryProtocol using the `MESI Protocol` wherein: 
* 2 unrelated variables are stored in the same cache line that are written to by 2 different cores often.
* This will generate a lot of invalidate/update traffic, slowing the system down. 