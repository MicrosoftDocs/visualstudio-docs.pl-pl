---
title: Zarządzanie pakietów VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702650"
---
# <a name="manage-vspackages"></a>Zarządzanie pakietami VSPackage
W większości przypadków nie trzeba martwić się o zarządzanie pakietów VSPackage, ponieważ szablony projektów i elementów rejestrują i ładują pakiet automatycznie. Jednak w niektórych sytuacjach może być konieczne poznanie nieco więcej informacji w celu zarządzania pakietem.

## <a name="use-the-experimental-instance"></a>Użyj wystąpienia eksperymentalnego
 Aby dowiedzieć się więcej o eksperymentalnym wystąpieniu, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Zarejestruj i Wyrejestruj pakietów VSPackage
 Aby dowiedzieć się, jak zarejestrować i wyrejestrować pakietów VSPackage oraz inne typy rozszerzeń, zobacz [Rejestrowanie i Wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Załaduj pakietu VSPackage
 Pakietów VSPackage można ustawić na automatyczne ładowanie, gdy określony identyfikator GUID CMDUICONTEXT jest włączony. Aby uzyskać więcej informacji, zobacz [Load pakietów VSPackage](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Użyj AsyncPackage do załadowania pakietów VSPackage w tle
 `AsyncPackage`Klasa umożliwia ładowanie pakietów w wątku w tle w celu uzyskania lepszej czas odpowiedzi interfejsu użytkownika w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: use AsyncPackage to load pakietów VSPackage w tle](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Kontekst interfejsu użytkownika oparty na regułach dla rozszerzeń
 Konteksty interfejsu użytkownika oparte na regułach umożliwiają autorom rozszerzeń Definiowanie precyzyjnych warunków, w których kontekst interfejsu użytkownika jest aktywowany i załadowanych skojarzonych pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [jak: używanie kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnozowanie wydajności rozszerzenia
Rozszerzenia mogą mieć wpływ na wydajność uruchamiania i ładowania rozwiązań. Dowiedz się, jak jest obliczany wpływ rozszerzenia programu Visual Studio i jak można go analizować lokalnie w celu przetestowania, jeśli rozszerzenie może być widoczne jako rozszerzenie wpływające na wydajność. Aby uzyskać więcej informacji, zobacz [How to: diagnozowanie wydajności rozszerzenia](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Rozwiązywanie problemów z pakietów VSPackage
 Poznaj techniki rozwiązywania problemów z pakietów VSPackage, które nie ładują ani nie występują błędy: [Rozwiązywanie problemów z pakietów VSPackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
