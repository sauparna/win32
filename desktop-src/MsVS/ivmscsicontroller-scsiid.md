---
title: IVMSCSIController SCSIID property
description: The SCSIID property contains the SCSI ID of the controller on a SCSI bus.
ms.assetid: a81572b1-b68f-4aaa-8353-a60fb0d24e93
keywords:
- SCSIID property Virtual Server
- SCSIID property Virtual Server , IVMSCSIController interface
- IVMSCSIController interface Virtual Server , SCSIID property
- SCSIID property Virtual Server , VMSCSIController interface
- VMSCSIController interface Virtual Server , SCSIID property
topic_type:
- apiref
api_name:
- IVMSCSIController.SCSIID
- IVMSCSIController.get_SCSIID
- VMSCSIController.SCSIID
api_location:
- VsComInterfaces.h
api_type:
- COM
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# IVMSCSIController::SCSIID property

The **SCSIID** property contains the SCSI ID of the controller on a SCSI bus.

This property is read-only.

## Syntax


```C++
HRESULT get_SCSIID(
  [out] long *SCSIID
);
```

<span codelanguage="VisualBasic"></span>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>VB</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><pre><code>VMSCSIController.SCSIID( _
  ByRef SCSIID _
)</code></pre></td>
</tr>
</tbody>
</table>



## Property value

The SCSI ID of the controller on a SCSI bus. This can either be 6 or 7.

This property value is read-only.

## Error codes



| Name                                                                                           | Meaning                                                                 |
|------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| <dl> <dt>S\_OK</dt> </dl>               | The operation was successful.<br/>                                |
| <dl> <dt>E\_POINTER</dt> </dl>          | The *SCSIID* parameter is **NULL**.<br/>                          |
| <dl> <dt> VM\_E\_VM\_UNKNOWN</dt> </dl> | The virtual machine for this SCSI controller does not exist.<br/> |
| <dl> <dt>DISP\_E\_EXCEPTION</dt> </dl>  | An unexpected error occurred.<br/>                                |



## Requirements



|                     |                                                                                                   |
|---------------------|---------------------------------------------------------------------------------------------------|
| Product<br/>  | Microsoft Virtual Server 2005 onWindows Server 2003<br/>                                    |
| Download<br/> | Microsoft Virtual Server 2005 R2 SP1 Update onWindows Server 2008orWindows Server 2003<br/> |
| Header<br/>   | <dl> <dt>VsComInterfaces.h</dt> </dl>      |



## See also

<dl> <dt>

[**IVMSCSIController**](ivmscsicontroller.md)
</dt> </dl>

 

 




