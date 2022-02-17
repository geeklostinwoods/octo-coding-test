# McAfee OCTO Kernel Test
The goal of the driver is receive and process file tracking requests. The IOCTL asks that a file be opened and information about the file be put onto a linked list [tracking_list_head_](Queue.c). This information will be used later by the driver. The request is described in the `TRACK_FILE` structure in [Public.h](Public.h).

The request is received via an [IOCTL](https://docs.microsoft.com/en-us/windows/win32/devio/device-input-and-output-control-ioctl-) code.

Candidates are expected to:
1. Define their own IOCTL code in (Public.h)[Public.h]
1. Verify the `TRACK_FILE` structure is valid and safe to use. Please note that this structure is always passed with NEITHER_IO.
1. Open the file provided in the `TRACK_FILE` structure.
1. Add the `TRACK_FILE` request to the linked list `track_file_list_head_`.

Please note that the linked list code has not yet been written, please use `LIST_ENTRY` or write your own. Also, do **note** that the linked list may be accessed by code running a `DISPATCH_LEVEL/DPC_LEVEL`.

Candidates should spend no more than 2 hours on this test. Successful submissions will take into account.

## Task Requirements
Only the driver need compile; we will not be testing the driver as part of this test.