---
title: Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33efc0bf393746a80b0881dacae01eaafe65bb8e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351625"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Określenia stanu polecenia przy użyciu zestawów międzyoperacyjnych
Pakietu VSPackage musi zachować informacje o stanie poleceń, które może obsłużyć. Środowisko nie może określić, kiedy polecenie przetwarzanych w ramach Twojego pakietu VSPackage staje się włączone lub wyłączone. Jest odpowiedzialny za Twojego pakietu VSPackage poinformować środowiska o stanach polecenia, na przykład stanu Generalny polecenia, takie jak **Wytnij**, **kopiowania**, i **Wklej**.

## <a name="status-notification-sources"></a>Stan powiadomienia źródeł
 Środowisko otrzymuje informacji na temat poleceń w pakietach VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody, która jest częścią pakietu VSPackage implementacji programu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Wywołania środowiska <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda pakietu VSPackage w dwóch okolicznościach:

- Gdy użytkownik otwiera menu głównego lub menu kontekstowego (na przykład przez kliknięcie prawym przyciskiem myszy), wykonuje środowiska <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody na wszystkich poleceń tym menu, aby określić ich stanu.

- Gdy pakietu VSPackage żąda, że środowisko aktualizacji bieżący interfejsu użytkownika (UI). Ta aktualizacja jest wykonywane jako polecenia, które są obecnie widoczne dla użytkownika, takich jak **Wytnij**, **kopiowania**, i **Wklej** grupowania na standardowym pasku narzędzi, stają się włączone i wyłączone w odpowiedzi na działania kontekstu i użytkownika.

  Ponieważ powłoki hostuje wiele pakietów VSPackage, wydajności powłoki programu nieakceptowalnie może obniżyć razie zostały sondować każdego pakietu VSPackage, aby określić stan polecenia. Zamiast tego Twojego pakietu VSPackage powinny aktywnie powiadomić środowiska, zmianie jego interfejsu użytkownika w momencie zmiany. Aby uzyskać więcej informacji na temat powiadomienie o aktualizacji, zobacz [zaktualizować interfejs użytkownika](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Stan: niepowodzenie powiadomień
 Błąd usługi pakietu VSPackage powiadomić środowiska zmiany stanu polecenia można umieścić interfejsu użytkownika w stanie niespójnym. Należy pamiętać, że dowolne polecenia menu menu lub kontekst można umieścić na pasku narzędzi przez użytkownika. W związku z tym aktualizowania interfejsu użytkownika, tylko wtedy, gdy zostanie otwarte menu menu lub kontekst nie jest wystarczająca.

## <a name="see-also"></a>Zobacz także
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementacja](../../extensibility/internals/command-implementation.md)