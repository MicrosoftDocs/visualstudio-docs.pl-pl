---
title: Określanie stanu polecenia przy użyciu zestawów interop | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708713"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych
VsPackage musi śledzić stan poleceń, które może obsłużyć. Środowisko nie może określić, kiedy polecenie obsługiwane w programie VSPackage zostanie włączone lub wyłączone. Obowiązkiem programu VSPackage jest informowanie środowiska o stanach poleceń, na przykład o stanie poleceń ogólnych, takich jak **Wytnij,** **Kopiuj**i **Wklej.**

## <a name="status-notification-sources"></a>Źródła powiadomień o stanie
 Środowisko odbiera informacje o poleceniach za pośrednictwem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody VSPackages, która jest częścią <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji interfejsu vspackage. Środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę VSPackage pod dwoma warunkami:

- Gdy użytkownik otworzy menu główne lub menu kontekstowe (klikając prawym przyciskiem myszy), środowisko wykonuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę na wszystkich poleceniach w tym menu, aby określić ich stan.

- Gdy VSPackage żąda, aby środowisko zaktualizować bieżący interfejs użytkownika (UI). Ta aktualizacja występuje, gdy polecenia, które są obecnie widoczne dla użytkownika, takie jak **Wytnij,** **Kopiuj**i **Wklej** grupowanie na standardowym pasku narzędzi, stają się włączone i wyłączone w odpowiedzi na działania kontekstu i użytkownika.

  Ponieważ powłoka obsługuje wiele VSPackages, wydajność powłoki będzie niedopuszczalnie obniżyć, jeśli były wymagane do sondowania każdego VSPackage do określenia stanu polecenia. Zamiast tego vspackage należy aktywnie powiadamiać środowisko, gdy jego interfejs użytkownika zmienia się w momencie zmiany. Aby uzyskać więcej informacji na temat powiadamiania o aktualizacji, zobacz [Aktualizowanie interfejsu użytkownika](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Niepowodzenie powiadomienia o stanie
 Niepowodzenie vspackage powiadomić środowisko o zmianie stanu polecenia można umieścić interfejsu użytkownika w niespójnym stanie. Pamiętaj, że użytkownik może umieścić na pasku narzędzi dowolne polecenia menu lub menu kontekstowego. W związku z tym aktualizowanie interfejsu użytkownika tylko wtedy, gdy menu lub menu kontekstowe otwiera się nie wystarczy.

## <a name="see-also"></a>Zobacz też
- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Wdrażanie](../../extensibility/internals/command-implementation.md)
