---
title: About Folder Monitoring
description: About Folder Monitoring
ms.assetid: d3d83e60-ecc7-4501-a6dd-15f7680a6ec9
keywords:
- Windows Media Player,folder monitoring
- Windows Media Player object model,folder monitoring
- object model,folder monitoring
- Windows Media Player ActiveX control,folder monitoring
- ActiveX control,folder monitoring
- Windows Media Player Mobile ActiveX control,folder monitoring
- Windows Media Player Mobile,folder monitoring
- folder monitoring
- monitoring folders
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# About Folder Monitoring

Windows Media Player can monitor folders that contain digital media files and update the library when files are added or removed. This folder monitoring functionality is provided by the [IWMPFolderMonitorServices](/windows/desktop/api/wmp/nn-wmp-iwmpfoldermonitorservices) interface.

To use the folder monitoring services, you must create the Player object in a remote state. For more information about remoting, see [Remoting the Windows Media Player Control](remoting-the-windows-media-player-control.md). After you have created a remoted instance of the player, obtain a pointer to the **IWMPFolderMonitorServices** interface by calling **QueryInterface** on the [IWMPPlayer](/windows/desktop/api/wmp/nn-wmp-iwmpplayer) interface.

Windows Media Player keeps a list of folders that are being monitored. To get a list of monitored folders, use the [IWMPFolderMonitorServices::get\_count](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-get_count) and [IWMPFolderMonitorServices::item](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-item) methods. To add folders to the list or remove them from the list, use the [IWMPFolderMonitorServices::add](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-add) and [remove](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-remove) methods, respectively.

**Starting a Scan**

Monitoring of folders is normally a background process that does not need to be called explicitly. If you want to actively scan a folder, call [IWMPFolderMonitorServices::startScan](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-startscan). You can stop a scan in progress with the [IWMPFolderMonitorServices::stopScan](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-stopscan) method.

**Retrieving the Folder Monitoring Status**

**IWMPFolderMonitorServices** provides functionality for retrieving the status of the folder monitoring process.

Folder scanning is done in two passes. In the first pass, the Player scans the folders named in the monitored folders list one by one and builds a list of files to be added to the library. In the second pass, it goes through the list of files and adds the files to the library, and also removes any media items from the library whose corresponding physical files have been deleted from the file system.

The [FolderScanStateChange](/windows/desktop/api/wmp/nf-wmp-iwmpevents3-folderscanstatechange) event is used to notify your program whenever the Player switches to a new state. You can also retrieve the current state by calling [get\_scanState](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-get_scanstate). When the first pass starts, the current state value is wmpfssScanning. During the second pass, the state switches to wmpfssUpdating. After the process is finished, the state changes to wmpfssStopped.

While the Player is scanning the monitored folders on the first pass, call [get\_scannedFilesCount](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-get_scannedfilescount) to check how many files have been scanned. The [get\_currentFolder](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-get_currentfolder) method will tell you which folder is currently being scanned.

After the second pass starts, call [get\_addedFilesCount](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-get_addedfilescount) to check how many files have been added to the library. The [get\_updateProgress](/windows/desktop/api/wmp/nf-wmp-iwmpfoldermonitorservices-get_updateprogress) method will tell you the progress of the second pass, as a percentage from 0 to 100.

## Related topics

<dl> <dt>

[**About the Player Object Model**](about-the-player-object-model.md)
</dt> <dt>

[**IWMPFolderMonitorServices Interface**](/windows/desktop/api/wmp/nn-wmp-iwmpfoldermonitorservices)
</dt> </dl>

 

 



