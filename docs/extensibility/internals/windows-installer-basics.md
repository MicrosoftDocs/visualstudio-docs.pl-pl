---
title: Podstawy Instalatora Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703416"
---
# <a name="windows-installer-basics"></a>Podstawowe informacje dotyczące Instalatora Windows
Instalator Windows instaluje i odinstalowuje aplikacje lub oprogramowanie na komputerze użytkownika, wykonując te zadania w jednostkach nazywanych składnikami Instalatora Windows (czasami nazywanymi WIC lub po prostu składnikami). Identyfikator GUID identyfikuje każdy WIC, który jest podstawową jednostką instalacji i zliczania odwołań dla konfiguracji przy użyciu Instalatora Windows.

 Aby uzyskać kompleksową dokumentację Instalatora Windows, zobacz temat SDK platformy, [Instalator Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Tworzenie pakietu VSPackage
 Instalator Windows używa pakietów instalacyjnych, które zawierają informacje, które Instalator Windows musi zainstalować, odinstalować lub naprawić produkt oraz uruchomić interfejs użytkownika instalatora. Każdy pakiet instalacyjny zawiera plik msi, który zawiera bazę danych instalacji, strumień informacji podsumowujących i strumienie danych dla różnych części instalacji. Aby korzystać z instalatora, należy autoryzować instalację. Ponieważ instalator organizuje instalacje wokół koncepcji składników i przechowuje informacje o instalacji w relacyjnej bazie danych, proces tworzenia pakietu instalacyjnego zasadniczo pociąga za sobą następujące kroki:

1. Zaplanuj tworzenie konfiguracji, aby wspierać przechowywanie wersji i strategie obok siebie.

2. Zidentyfikuj funkcje, które mają być prezentowane użytkownikom.

3. Organizowanie VSPackage i zależności w składniki.

4. Wypełnij bazę danych instalacji informacjami.

5. Sprawdź poprawność pakietu instalacyjnego.

   Dokumentacja ta dotyczy przede wszystkim pierwszego i trzeciego stopnia procesu. Podczas tych kroków organizujesz funkcje VSPackage w WIC, dzięki czemu można oprawić [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]w ramę strategię przechowywania wersji i obsługi, aby uwzględnić kolejne wersje programu . Pozostałe trzy kroki są szczegółowo opisane w dokumentacji Instalatora Windows w sdk platformy.

## <a name="key-terms"></a>Kluczowe terminy
 Poniżej przedstawiono definicje kluczowych terminów związanych z technologią Instalatora Windows.

 Pliki zasobów, klucze rejestru, skróty lub tak dalej, które mogą być zainstalowane na komputerze. Zasoby te są logicznie grupowane w składniki Instalatora Windows.

 Składnik Instalatora Windows (WIC) Podstawowa jednostka instalacji reprezentująca logiczne grupowanie powiązanych zasobów, które są instalowane i odinstalowywane jako jednostka. Składniki Instalatora Windows są identyfikowane za pomocą unikatowego identyfikatora składnika lub identyfikatora GUID. Ponadto Instalator Windows utrzymuje swoje zliczanie odniesienia na poziomie WIC. Aby uzyskać maksymalną elastyczność przechowywania wersji, dołącz nie więcej niż jeden zasób podstawowy, taki jak biblioteka DLL, w danym WIC. Należy zauważyć, że po zidentyfikowaniu i wypełnieniu WIC, nadaj mu identyfikator GUID i wdrażaj go, nie można zmienić jego składu. Aby uzyskać więcej informacji, zobacz [Organizowanie aplikacji w składniki](/windows/desktop/Msi/organizing-applications-into-components).

 Pakiet (pakiet Redist) Jednostka wdrożenia, która składa się z pliku msi i zewnętrznych plików źródłowych, do których ten plik może wskazywać. Pakiet zawiera wszystkie informacje potrzebne Instalatorowi Windows do uruchomienia interfejsu użytkownika oraz zainstalowania lub odinstalowania aplikacji.

 .msi Plik A COM-structured storage file containing the instructions and data required to install an application. Każdy pakiet zawiera co najmniej jeden plik msi. Plik msi zawiera bazę danych instalatora, strumień informacji podsumowujących i ewentualnie jeden lub więcej przekształceń i wewnętrznych plików źródłowych. Pliki, które mają być zainstalowane, mogą być skompresowane do szafy i przechowywane w strumieniu w pliku msi lub przechowywane, kompresowane lub nieskompresowane poza plikiem .msi na nośniku źródłowym. Aby uzyskać więcej informacji, zobacz [Rozszerzenia plików Instalatora Windows](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Wymuszanie reguł instalatora Windows
 Dwa zestawy reguł określają wdrażanie zasobów za pośrednictwem składników konfiguracji. Jeden zestaw reguł jest obsługiwany przez samego Instalatora Windows, podczas gdy drugi zestaw należy wymusić jako autor instalacji.

> [!NOTE]
> Wymuszanie reguł Instalatora Windows występuje tylko po uruchomieniu sprawdzania poprawności pliku msi. Niemniej jednak, są ostrzegani, aby traktować te zasady jako najlepsze praktyki. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności bazy danych instalacji](/windows/desktop/Msi/validating-an-installation-database) i sprawdzania poprawności [pakietu](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Reguły wymuszone przez instalatora

- Wszystkie pliki w danym składniku muszą być zainstalowane w tym samym katalogu. Z drugiej strony pliki zainstalowane w oddzielnych folderach muszą należeć do oddzielnych składników.

- Może istnieć tylko jedna ścieżka klucza na składnik. Ścieżka klucza jest po prostu kluczem pliku lub rejestru, który reprezentuje cały składnik.

#### <a name="component-provider-responsibilities"></a>Obowiązki dostawcy komponentu

- Wszelkie dwa zasoby, które mogą być dostarczane oddzielnie w kolejnych wersjach powinny istnieć w oddzielnych komponentach. Zasoby powinny być pogrupowane w ten sam składnik tylko wtedy, gdy masz pewność, że te zasoby nigdy nie będą dostarczane oddzielnie. W rzeczywistości zaleca się, aby wszystkie zasoby podstawowe (na przykład biblioteki DLL) zawsze istniały w oddzielnych wic. Aby uzyskać więcej informacji, zobacz [Definiowanie składników instalatora](/windows/desktop/Msi/defining-installer-components).

- Żaden wersja nie powinna być wysyłana w więcej niż jednym WIC.

## <a name="see-also"></a>Zobacz też
- [Co się stanie, jeśli reguły składników są łamane?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
