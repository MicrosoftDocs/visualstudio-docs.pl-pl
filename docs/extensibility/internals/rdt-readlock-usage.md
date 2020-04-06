---
title: Użycie RDT_ReadLock | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705930"
---
# <a name="rdt_readlock-usage"></a>Użycie flagi RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) jest flagą, która zawiera logikę blokowania dokumentu w uruchomionej tabeli dokumentów (RDT), która jest listą wszystkich dokumentów, które są obecnie otwarte w programie Visual Studio IDE. Ta flaga określa, kiedy dokumenty są otwierane i czy dokument jest widoczny w interfejsie użytkownika lub przechowywany niewidocznie w pamięci.

Ogólnie rzecz biorąc, używasz [_VSRDTFLAGS. RDT_ReadLock,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) gdy spełniony jest jeden z następujących elementów:

- Chcesz otworzyć dokument niewidocznie i tylko do odczytu, ale <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nie jest jeszcze ustalona, która powinna być jego właścicielem.

- Chcesz, aby użytkownik został poproszony o zapisanie dokumentu, który został niewidocznie otwarty, zanim użytkownik wyświetli go w interfejsie użytkownika, a następnie podjął próbę jego zamknięcia.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Jak zarządzać widocznymi i niewidocznymi dokumentami

Gdy użytkownik otworzy dokument w interfejsie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> użytkownika, należy ustanowić właściciela dokumentu i [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) flaga musi być ustawiona. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nie można ustanowić żadnego właściciela, dokument nie zostanie zapisany po kliknięciu przez użytkownika **przycisku Zapisz wszystko** lub zamknięciu IDE. Oznacza to, że jeśli dokument jest otwarty niewidocznie, gdzie jest modyfikowany w pamięci, a użytkownik jest monitowany `RDT_ReadLock` o zapisanie dokumentu na zamknięciu lub zapisane, jeśli **wybrano Zapisz wszystko,** nie można go użyć. Zamiast tego należy użyć `RDT_EditLock` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> zarejestrować, gdy [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) flaga.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock i modyfikacja dokumentu

Poprzednia wspomniana flaga wskazuje, że niewidoczne `RDT_EditLock` otwarcie dokumentu spowoduje jego uzyskanie po otwarciu dokumentu przez użytkownika do widocznego **pliku DocumentWindow**. W takim przypadku użytkownik jest wyświetlany z **zapisz** monit, gdy widoczny **DocumentWindow** jest zamknięty. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`implementacje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> które korzystają z `RDT_ReadLock` usługi początkowo działają, gdy jest pobierana tylko (tj. gdy dokument jest otwierany niewidocznie w celu przeanalizowania informacji). Później, jeśli dokument musi zostać zmodyfikowany, blokada zostanie uaktualniona do słabego **RDT_EditLock**. Jeśli użytkownik następnie otworzy dokument w widocznym **DocumentWindow**, `CodeModel`'s słaby `RDT_EditLock` jest zwolniony.

Jeśli użytkownik następnie zamyka **DocumentWindow** i wybiera **nie** po wyświetleniu monitu `CodeModel` o zapisanie otwartego dokumentu, implementacja usuwa wszystkie informacje w dokumencie i niewidocznie ponownie otwiera dokument z dysku, gdy następnym razem więcej informacji jest wymagane dla dokumentu. Subtelność tego zachowania jest wystąpieniem, w którym użytkownik otwiera **Okno DocumentWindow** niewidocznego otwartego dokumentu, modyfikuje go, zamyka, a następnie wybiera **nie** po wyświetleniu monitu o zapisanie dokumentu. W takim przypadku, jeśli `RDT_ReadLock`dokument ma , dokument nie zostanie faktycznie zamknięty, a zmodyfikowany dokument pozostanie niewidocznie otwarty w pamięci, nawet jeśli użytkownik nie zdecydował się zapisać dokumentu.

Jeśli niewidoczny otwór dokumentu `RDT_EditLock`używa słabego , daje blokadę, gdy użytkownik otwiera dokument w widoczny sposób i nie są przechowywane żadne inne blokady. Gdy użytkownik zamknie **DocumentWindow** i wybierze **nie** po wyświetleniu monitu o zapisanie dokumentu, dokument musi zostać zamknięty z pamięci. Oznacza to, że klient niewidoczny musi nasłuchiwać zdarzeń RDT, aby śledzić to wystąpienie. Następnym razem, gdy dokument jest wymagany, dokument musi zostać ponownie otwarty.
