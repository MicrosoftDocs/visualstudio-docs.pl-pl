---
title: RDT_ReadLock Usage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c11cee4c1f8c150fc8bcf42b3dbc1a193d3441a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341357"
---
# <a name="rdtreadlock-usage"></a>Użycie flagi RDT_ReadLock

[_VSRDTFLAGS. Flagi RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) jest flaga, która udostępnia logikę blokowania dokumentu w systemem dokumentu tabeli (Normalizacją), który znajduje się lista wszystkich dokumentów, które są aktualnie otwarte w środowisku IDE programu Visual Studio. Ta flaga Określa, kiedy są otwarte dokumenty i tego, czy dokument jest widoczne w interfejsie użytkownika lub które odbyło się w sposób niewidoczny w pamięci.

Ogólnie rzecz biorąc, możesz użyć [_VSRDTFLAGS. Flagi RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) gdy jest spełniony jeden z następujących czynności:

- Chcesz otworzyć dokument w sposób niewidoczny i tylko do odczytu, ale go nie jest jeszcze nawiązane, który <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> należy jej właścicielem.

- Chcesz, aby użytkownikowi monit o zapisanie dokumentów, którą otwarto w sposób niewidoczny przed użytkownika on wyświetlany w interfejsie użytkownika, a następnie podjęto próbę je zamknąć.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Jak zarządzać widoczne i niewidoczne dokumentów

Gdy użytkownik otwiera dokument w interfejsie użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> właściciela dokumentu należy ustanowić i [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) musi zostać ustawiona flaga. Jeśli nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> może zostać nawiązana właściciela, a następnie nie będzie można zapisać dokumentu, gdy użytkownik kliknie **Zapisz wszystko** lub zamyka IDE. Oznacza to, czy dokument jest otwarty niewidocznie w przypadku, gdy zostanie zmodyfikowany w pamięci, a użytkownik jest monitowany o zapisanie dokumentu podczas zamykania lub zapisany, jeśli **Zapisz wszystko** zostanie wybrana, a następnie `RDT_ReadLock` nie mogą być używane. Zamiast tego należy użyć `RDT_EditLock` i Zarejestruj <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> podczas [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) flagi.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock i modyfikacja dokumentu

Poprzednie flagę wymienione wskazuje, przyniesie niewidoczne otwarcia dokumentu jego `RDT_EditLock` po otwarciu dokumentu przez użytkownika do widocznych **DocumentWindow**. W takiej sytuacji użytkownik zobaczy **Zapisz** monitowanie, gdy widoczny **DocumentWindow** jest zamknięty. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` implementacje, które używają <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> usługa początkowo działać, gdy tylko `RDT_ReadLock` jest zajęta (tj. gdy dokument jest otwarty w sposób niewidoczny można przeanalizować informacji). Później, jeśli muszą zostać zmodyfikowane w dokumencie, następnie blokada została uaktualniona do ograniczymy **RDT_EditLock**. Jeśli następnie użytkownik otwiera dokument w widoczne **DocumentWindow**, `CodeModel`firmy słabe `RDT_EditLock` wydaniu.

Jeśli użytkownik jest następnie zamknie **DocumentWindow** i wybiera **nie** po wyświetleniu monitu o Zapisz otwarty dokument, a następnie `CodeModel` implementacji usuwa wszystkie informacje w dokumencie i ponownie otworzy dokument z dysku niewidocznie przy następnym więcej informacji jest wymagane dla dokumentu. Subtlety to zachowanie jest wystąpieniem, gdy użytkownik otwiera **DocumentWindow** niewidoczne otwartego dokumentu, modyfikuje je, zamyka te błędy, a następnie **nie** po wyświetleniu monitu o zapisanie dokumentu. W tym przypadku, jeśli dokument ma `RDT_ReadLock`, a następnie dokumentu nie zostaną rzeczywiście zamknięte i zmodyfikowanego dokumentu pozostanie otwarte w sposób niewidoczny w pamięci, nawet jeśli użytkownik wybrał nie można zapisać dokumentu.

Jeśli niewidoczne otwarcia dokumentu używa ograniczymy `RDT_EditLock`, a następnie daje blokady, gdy użytkownik otwiera dokument widoczny blokady nie są aktywne. Gdy użytkownik zamknie **DocumentWindow** i wybiera **nie** po wyświetleniu monitu można zapisać dokumentu, następnie należy zamknąć dokument z pamięci. Oznacza to, że niewidoczne klienta musi nasłuchiwać zdarzeń Normalizacją w celu śledzenia tego wystąpienia. Podczas następnego dokumentu jest wymagany, dokumentu musi można ponownie otworzyć.