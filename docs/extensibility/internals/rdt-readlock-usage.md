---
title: Użycie RDT_ReadLock | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705930"
---
# <a name="rdt_readlock-usage"></a>Użycie flagi RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) jest flagą, która zapewnia logikę blokowania dokumentu w uruchomionej tabeli dokumentu (RDT), która jest listą wszystkich dokumentów, które są aktualnie otwarte w środowisku IDE programu Visual Studio. Ta flaga określa, kiedy dokumenty są otwierane oraz czy dokument jest widoczny w interfejsie użytkownika, czy też jest przechowywany w pamięci.

Ogólnie rzecz biorąc używasz [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) , gdy jest spełniony jeden z następujących warunków:

- Chcesz otworzyć dokument niewidoczny i tylko do odczytu, ale nie został jeszcze ustanowiony, który powinien być <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> jego własnością.

- Chcesz, aby użytkownik był monitowany o zapisanie dokumentu, który był w niewidoczny sposób otwarty przed wyświetleniem go w INTERFEJSie użytkownika, a następnie podjęto próbę jego zamknięcia.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Jak zarządzać widocznymi i niewidocznymi dokumentami

Gdy użytkownik otwiera dokument w interfejsie użytkownika, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> musi zostać ustanowiony właściciel dokumentu oraz [_VSRDTFLAGS. Flaga RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) musi być ustawiona. Jeśli nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> można nawiązać żadnego właściciela, dokument nie zostanie zapisany, gdy użytkownik kliknie pozycję **Zapisz wszystko** lub zamknie IDE. Oznacza to, że dokument jest otwarty w niewidocznym miejscu, w którym jest modyfikowany w pamięci, a użytkownik jest monitowany o zapisanie dokumentu po zamknięciu lub zapisanie, jeśli wybrano opcję **Zapisz wszystko** , `RDT_ReadLock` nie można użyć. Zamiast tego należy użyć `RDT_EditLock` i zarejestrować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> gdy [__VSREGDOCLOCKHOLDER. Flaga RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) .

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock i modyfikacja dokumentu

Poprzednia Flaga wskazuje, że niewidzialne otwarcie dokumentu spowoduje jego wyświetlenie, `RDT_EditLock` gdy dokument zostanie otwarty przez użytkownika w widocznym **DocumentWindow**. W takim przypadku użytkownik zobaczy monit o **zapis** , gdy widoczny **DocumentWindow** jest zamknięty. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` implementacje korzystające z <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> usługi początkowo działały, gdy tylko `RDT_ReadLock` zostanie podjęta (tj., gdy dokument zostanie otwarty w sposób niewidoczny do analizy informacji). Później, jeśli dokument należy zmodyfikować, blokada zostanie uaktualniona do słabego **RDT_EditLock**. Jeśli użytkownik otworzy dokument w widocznym **DocumentWindow**, zostanie wyświetlona wartość `CodeModel` słabe `RDT_EditLock` .

Jeśli użytkownik zamknie **DocumentWindow** i wybierze opcję **nie** po wyświetleniu monitu o zapisanie otwartego dokumentu, `CodeModel` implementacja usuwa wszystkie informacje w dokumencie i ponownie otwiera dokument z dysku, gdy następnym razem więcej informacji jest wymaganych dla dokumentu. Subtlety tego zachowania jest wystąpieniem, w którym użytkownik otwiera **DocumentWindow** niewidocznego otwartego dokumentu, modyfikuje go, zamyka, a następnie wybiera **nie** po wyświetleniu monitu o zapisanie dokumentu. W takim przypadku, jeśli dokument zawiera `RDT_ReadLock` , wówczas dokument nie zostanie zamknięty, a zmodyfikowany dokument pozostanie otwarty w pamięci, nawet jeśli użytkownik nie zapisał dokumentu.

Jeśli niewidzialne otwarcie dokumentu używa słabego `RDT_EditLock` , wówczas zostanie ono zablokowane, gdy użytkownik otworzy dokument w widocznym czasie i nie są przechowywane żadne inne blokady. Gdy użytkownik zamknie **DocumentWindow** i wybierze **nie** po wyświetleniu monitu o zapisanie dokumentu, dokument musi być zamknięty z pamięci. Oznacza to, że niewidoczny klient musi nasłuchiwać zdarzeń RDT, aby śledzić to wystąpienie. Przy następnym uruchomieniu dokumentu należy ponownie otworzyć dokument.
