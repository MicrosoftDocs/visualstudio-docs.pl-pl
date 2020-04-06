---
title: Zagadnienia dotyczące rozładunku i przeładunku projektów zagnieżdżonych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709287"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Zagadnienia dotyczące rozładunku i przeładunku projektów zagnieżdżonych

Podczas implementowania zagnieżdżonych typów projektów, należy wykonać dodatkowe kroki podczas zwalniania i ponownego ładowania projektów. Aby poprawnie powiadomić detektory o zdarzeniach `OnBeforeUnloadProject` `OnAfterLoadProject` rozwiązania, należy poprawnie podnieść i zdarzenia.

Jednym z powodów, aby podnieść te zdarzenia jest kontroli kodu źródłowego (SCC). Nie chcesz SCC usunąć elementy z serwera, a następnie dodać je z `Get` powrotem jako *nowe,* jeśli istnieje operacja z SCC. W takim przypadku nowy plik zostanie załadowany z SCC. Musisz zwolnić i ponownie załadować wszystkie pliki w przypadku, gdy są one różne.

Wywołania `ReloadItem`kontroli kodu źródłowego . Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfejs do wywołania `OnBeforeUnloadProject` i `OnAfterLoadProject` usunięcia projektu i ponownego utworzenia go. Po zaimplementowanie interfejsu w ten sposób, SCC jest informowany, że projekt został tymczasowo usunięty i dodany ponownie. W związku z tym SCC nie działa na projekcie tak, jakby projekt został *faktycznie* usunięty i ponownie dodany.

## <a name="reload-projects"></a>Przeładuj projekty

Aby obsługiwać ponowne ładowanie projektów zagnieżdżonych, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodę. W implementacji `ReloadItem`programu zamknij projekty zagnieżdżone, a następnie ponownie je tworzysz.

Zazwyczaj, gdy projekt jest ponownie załadowany, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> wywołuje i zdarzenia. Jednak dla projektów zagnieżdżonych, które są usuwane i ponownie załadowany, projekt nadrzędny inicjuje proces, a nie IDE. Ponieważ projekt nadrzędny nie wywołuje zdarzeń rozwiązania, a IDE nie ma informacji o inicjalizacji procesu, zdarzenia nie są wywoływane.

Aby obsłużyć ten `QueryInterface` proces, projekt nadrzędny wywołuje interfejs. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> `IVsFireSolutionEvents`ma funkcje, które mówią `OnBeforeUnloadProject` IDE do podniesienia zdarzenia, aby `OnAfterLoadProject` zwolnić zagnieżdżonego projektu, a następnie podnieść zdarzenie, aby ponownie załadować tego samego projektu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Projekty nest](../../extensibility/internals/nesting-projects.md)
