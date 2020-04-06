---
title: Zarządzanie komponentami | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709337"
---
# <a name="component-management"></a>Zarządzanie komponentami
Jednostki zadań w Instalatorze Windows są określane jako składniki Instalatora Windows (czasami nazywane WIC lub po prostu składniki). Identyfikator GUID identyfikuje każdy WIC, który jest podstawową jednostką instalacji i zliczania odwołań dla konfiguracji korzystających z Instalatora Windows.

 Chociaż do utworzenia instalatora vsPackage można użyć kilku produktów, w tej dyskusji przyjęto użycie plików Instalatora Windows (*msi).* Podczas tworzenia instalatora należy poprawnie zarządzać wdrożeniem plików, aby poprawne zliczanie odwołań odbywa się przez cały czas. W związku z tym różne wersje produktu nie będzie kolidować z lub złamać siebie w kombinacji scenariuszy instalacji i odinstalowywania.

 W Instalatorze Windows zliczanie odwołań odbywa się na poziomie składnika. Należy starannie zorganizować zasoby — pliki, wpisy rejestru i tak dalej — w składniki. Istnieją inne poziomy organizacji — takie jak moduły, funkcje i produkty — które mogą pomóc w różnych scenariuszach. Aby uzyskać więcej informacji, zobacz [Podstawowe informacje o Instalatorze Windows](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Wskazówki dotyczące konfiguracji tworzenia do instalacji obok siebie

- Tworzenie plików i kluczy rejestru, które są współużytkowane przez wersje do własnych składników.

     Pozwala to łatwo spożywać je w następnej wersji. Na przykład wpisz biblioteki, które są zarejestrowane globalnie, rozszerzenia plików, inne elementy zarejestrowane w **HKEY_CLASSES_ROOT**i tak dalej.

- Grupowanie udostępnionych komponentów w oddzielne moduły scalania.

     Ta strategia pomaga poprawnie tworzyć instalację side-by-side posuwając się do przodu.

- Zainstaluj udostępnione pliki i klucze rejestru przy użyciu tych samych składników Instalatora Windows w różnych wersjach.

     Jeśli używasz innego składnika, pliki i wpisy rejestru są odinstalowywane po odinstalowaniu jednego wersji VSPackage, ale inny vspackage jest nadal zainstalowany.

- Nie mieszaj elementów wersjonowanych i udostępnionych w tym samym składniku.

     W ten sposób uniemożliwia zainstalowanie elementów udostępnionych w lokalizacji globalnej i wersjonowanych elementów w odizolowanych lokalizacjach.

- Nie ma udostępnionych kluczy rejestru wskazujących pliki wersjonowane.

     Jeśli to zrobisz, klucze udostępnione zostaną zastąpione po zainstalowaniu innego wersji VSPackage. Po usunięciu drugiej wersji plik, do którego wskazuje klucz, zniknął.

## <a name="see-also"></a>Zobacz też
- [Wybierz między pakietami współużytkowanymi i wersjonowanymi pakietami VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scenariusze konfiguracji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
