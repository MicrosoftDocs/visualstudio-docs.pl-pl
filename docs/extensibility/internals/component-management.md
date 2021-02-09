---
title: Zarządzanie składnikami | Microsoft Docs
description: Dowiedz się, jak zarządzać składnikami Instalator Windows podczas tworzenia Instalatora pakietu VSPackage w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44ee1a3afe313cdc11bb28e0a24a89e3e3ad7f0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852729"
---
# <a name="component-management"></a>Zarządzanie składnikami
Jednostki zadań w Instalator Windows są określane jako składniki Instalator Windows (czasami nazywane WICs lub tylko składnikami). Identyfikator GUID identyfikuje każdy WIC, który jest podstawową jednostką instalacji i zliczania odwołań dla konfiguracji, które używają Instalator Windows.

 Mimo że można użyć kilku produktów do utworzenia Instalatora pakietu VSPackage, w tej dyskusji założono użycie plików Instalator Windows (*MSI*). Podczas tworzenia Instalatora należy prawidłowo zarządzać wdrożeniem plików, tak aby poprawne zliczanie odwołań było wykonywane przez cały czas. W związku z tym różne wersje produktu nie zakłócają działania ani nie przerywają sobie nawzajem w ramach różnych scenariuszy instalacji i odinstalowywania.

 W Instalator Windows, zliczanie odwołań odbywa się na poziomie składnika. Należy starannie organizować zasoby — pliki, wpisy rejestru i tak dalej — w składnikach. Istnieją inne poziomy organizacji — takie jak moduły, funkcje i produkty, które mogą pomóc w różnych scenariuszach. Aby uzyskać więcej informacji, zobacz [podstawy Instalator Windows](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Wskazówki dotyczące instalacji tworzenia w celu zainstalowania równoczesnego

- Twórz pliki i klucze rejestru, które są współużytkowane przez wersje w ich własnych składnikach.

     Dzięki temu można łatwo korzystać z nich w następnej wersji. Na przykład typy bibliotek, które są rejestrowane globalnie, rozszerzenia plików, inne elementy zarejestrowane w **HKEY_CLASSES_ROOT** itd.

- Grupuj składniki współużytkowane w oddzielne moduły scalania.

     Ta strategia ułatwia samodzielne tworzenie instalacji równoległej do przodu.

- Zainstaluj udostępnione pliki i klucze rejestru, korzystając z tych samych składników Instalator Windows w różnych wersjach.

     W przypadku korzystania z innego składnika pliki i wpisy rejestru są odinstalowywane po odinstalowaniu jednej wersji pakietu VSPackage, ale nadal jest zainstalowana inna pakietu VSPackage.

- Nie mieszaj wersji i elementów udostępnionych w tym samym składniku.

     Dzięki temu nie można instalować elementów udostępnionych do lokalizacji globalnej i elementów z wersjami w odizolowanych lokalizacjach.

- Nie mają udostępnionych kluczy rejestru, które wskazują na pliki z wersjami.

     W takim przypadku klucze udostępnione zostaną nadpisywane, gdy zostanie zainstalowana inna wersja programu pakietu VSPackage. Po usunięciu drugiej wersji plik, w którym znajduje się klucz, został usunięty.

## <a name="see-also"></a>Zobacz też
- [Wybierz między udostępnionym i z wersją pakietów VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
