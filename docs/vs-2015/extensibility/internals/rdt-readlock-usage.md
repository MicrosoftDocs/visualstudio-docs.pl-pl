---
title: RDT_ReadLock Usage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9a6b5f86f0cfbb71f6264bdc74df72ad9209c9d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070163"
---
# <a name="rdtreadlock-usage"></a>Użycie flagi RDT_ReadLock
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> jest flagę, która udostępnia logikę blokowania dokumentu w systemem dokumentu tabeli (Normalizacją), który znajduje się lista wszystkich dokumentów, które są aktualnie otwarte w środowisku IDE programu Visual Studio. Ta flaga Określa, kiedy są otwarte dokumenty i tego, czy dokument jest widoczne w interfejsie użytkownika lub które odbyło się w sposób niewidoczny w pamięci.  
  
 Ogólnie rzecz biorąc, należy użyć <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> gdy jest spełniony jeden z następujących czynności:  
  
- Kiedy chcesz otworzyć dokument w sposób niewidoczny i tylko do odczytu, ale go nie jest jeszcze nawiązane, który <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> należy jej właścicielem.  
  
- Kiedy chcesz użytkownikowi monit o zapisanie dokumentów, którą otwarto w sposób niewidoczny przed użytkownika on wyświetlany w interfejsie użytkownika, a następnie podjęto próbę je zamknąć.  
  
## <a name="how-to-manage-visible-and-invisible-documents"></a>Jak zarządzać widoczne i niewidoczne dokumentów  
 Gdy użytkownik otwiera dokument w interfejsie użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> właściciela dokumentu należy ustanowić i <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> musi zostać ustawiona flaga. Jeśli nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> może zostać nawiązana właściciela, a następnie nie będzie można zapisać dokumentu, gdy użytkownik kliknie **Zapisz wszystko** lub zamyka IDE. Oznacza to, czy dokument jest otwarty niewidocznie w przypadku, gdy zostanie zmodyfikowany w pamięci, a użytkownik jest monitowany o zapisanie dokumentu podczas zamykania lub zapisany, jeśli **Zapisz wszystko** zostanie wybrana, a następnie `RDT_ReadLock` nie mogą być używane. Zamiast tego należy użyć `RDT_EditLock` i Zarejestruj <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> podczas <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> flagi.  
  
## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock i modyfikacja dokumentu  
 Poprzednie flagę wymienione wskazuje, przyniesie niewidoczne otwarcia dokumentu jego `RDT_EditLock` po otwarciu dokumentu przez użytkownika do widocznych **DocumentWindow**. W takiej sytuacji użytkownik zobaczy **Zapisz** monitowanie, gdy widoczny **DocumentWindow** jest zamknięty. Implementacje Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel, które używają <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> usługa początkowo działać, gdy tylko `RDT_ReadLock` jest zajęta (tj. gdy dokument jest otwarty w sposób niewidoczny można przeanalizować informacji). Później, jeśli muszą zostać zmodyfikowane w dokumencie, następnie blokada została uaktualniona do ograniczymy **RDT_EditLock**. Jeśli następnie użytkownik otwiera dokument w widoczne **DocumentWindow**, `CodeModel`firmy słabe `RDT_EditLock` wydaniu.  
  
 Jeśli użytkownik jest następnie zamknie **DocumentWindow** i wybiera **nie** po wyświetleniu monitu o Zapisz otwarty dokument, a następnie `CodeModel` implementacji usuwa wszystkie informacje w dokumencie i ponownie otworzy dokument z dysku niewidocznie przy następnym więcej informacji jest wymagane dla dokumentu. Subtlety to zachowanie jest wystąpieniem, gdy użytkownik otwiera **DocumentWindow** niewidoczne otwartego dokumentu, modyfikuje je, zamyka te błędy, a następnie **nie** po wyświetleniu monitu o zapisanie dokumentu. W tym przypadku, jeśli dokument ma `RDT_ReadLock`, a następnie dokumentu nie zostaną rzeczywiście zamknięte i zmodyfikowanego dokumentu pozostanie otwarte w sposób niewidoczny w pamięci, nawet jeśli użytkownik wybrał nie można zapisać dokumentu.  
  
 Jeśli niewidoczne otwarcia dokumentu używa ograniczymy `RDT_EditLock`, a następnie daje blokady, gdy użytkownik otwiera dokument widoczny blokady nie są aktywne. Gdy użytkownik zamknie **DocumentWindow** i wybiera **nie** po wyświetleniu monitu można zapisać dokumentu, następnie należy zamknąć dokument z pamięci. Oznacza to, że niewidoczne klienta musi nasłuchiwać zdarzeń Normalizacją w celu śledzenia tego wystąpienia. Podczas następnego dokumentu jest wymagany, dokumentu musi można ponownie otworzyć.
