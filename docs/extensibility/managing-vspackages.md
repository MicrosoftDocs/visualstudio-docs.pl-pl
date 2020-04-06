---
title: Zarządzanie pakietami VS | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702650"
---
# <a name="manage-vspackages"></a>Zarządzanie pakietami VSPackage
W większości przypadków nie musisz się martwić o zarządzanie pakietami VSPackages, ponieważ szablony projektu i elementów rejestrują się i ładują pakiet automatycznie. Jednak w niektórych okolicznościach może być konieczne, aby dowiedzieć się nieco więcej, aby zarządzać pakietem.

## <a name="use-the-experimental-instance"></a>Użyj wystąpienia eksperymentalnego
 Aby dowiedzieć się więcej o wystąpieniu eksperymentalnym, zobacz [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Rejestrowanie i wyrejestrowywanie pakietów VSPackage
 Aby dowiedzieć się, jak zarejestrować i wyrejestrować pakiety VSPackages i inne typy rozszerzeń, zobacz [Rejestrowanie i wyrejestrowanie pakietów VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Załaduj pakiet VSPackage
 VsPackages można ustawić na automatyczne ładowanie, gdy określony identyfikator GUID CMDUICONTEXT jest włączony. Aby uzyskać więcej informacji, zobacz [Ładowanie pakietów VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Za pomocą AsyncPackage załadować pakiety VSPackages w tle
 Klasa `AsyncPackage` umożliwia ładowanie pakietu w wątku w tle dla lepszej responsywności interfejsu użytkownika w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Jak: Użyj AsyncPackage do ładowania vspackages w tle](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Kontekst interfejsu użytkownika oparty na regułach dla rozszerzeń
 Konteksty interfejsu użytkownika oparte na regułach umożliwia autorom rozszerzeń zdefiniowanie dokładnych warunków, w których kontekst interfejsu użytkownika jest aktywowany i skojarzone vspackages załadowany. Aby uzyskać więcej informacji, zobacz [Jak: Użyj kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnozowanie wydajności rozszerzenia
Rozszerzenia mogą mieć wpływ na wydajność uruchamiania i ładowania rozwiązań. Dowiedz się, jak wpływ rozszerzenia programu Visual Studio jest obliczany i jak można go analizować lokalnie, aby przetestować, czy rozszerzenie może być wyświetlane jako rozszerzenie wpływające na wydajność. Aby uzyskać więcej informacji, zobacz [Jak: Diagnozowanie wydajności rozszerzenia](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Rozwiązywanie problemów z pakietami VSPackage
 Poznaj techniki rozwiązywania problemów z pakietami VSPackage, które nie ładują się lub występują błędy: [Rozwiązywanie problemów z pakietami VSPackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
