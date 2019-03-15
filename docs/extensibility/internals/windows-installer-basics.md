---
title: Podstawowe informacje o Windows Installer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2712c8d52ffd569f7d422708de612ac322045f8
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57872956"
---
# <a name="windows-installer-basics"></a>Podstawowe informacje dotyczące Instalatora Windows
Instalator Windows instaluje i odinstalowuje aplikacje lub produkty oprogramowania na komputerze użytkownika wykonywania tych zadań w jednostce o nazwie składniki Instalatora Windows (czasami nazywany WICs lub po prostu składników). Identyfikator GUID identyfikuje każdy składnik WIC to podstawowa jednostka instalacji i zliczanie dla konfiguracji za pomocą Instalatora Windows.

 Pełna dokumentacja Instalatora Windows na ten temat można znaleźć w temacie zestawu SDK platformy [Instalatora Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Tworzenie pakietu VSPackage
 Instalator Windows używa pakietów instalacyjnych, które zawierają informacje wymagające Instalatora Windows, aby zainstalować, odinstalować lub napraw produkt oraz do uruchamiania Instalatora interfejsu użytkownika (UI). Każdy pakiet instalacyjny zawiera plik msi, który zawiera bazę danych instalacji, strumień informacji podsumowujących i strumieni danych dla różnych części instalacji. Aby użyć Instalatora, możesz tworzyć instalacji. Ponieważ Instalator organizuje instalacje myślą o składniki i przechowuje informacje o instalacji w relacyjnej bazie danych, proces tworzenia pakietu instalacyjnego szeroko pociąga za sobą następujące czynności:

1. Planowanie ustawień tworzenia do obsługi wersji i strategie side-by-side.

2. Identyfikowanie funkcji, które mają zostać wyświetlone użytkownikom.

3. Organizuj pakietu VSPackage i zależności w składników.

4. Wypełnianie bazy danych instalacji z informacjami.

5. Sprawdzanie poprawności pakietu instalacyjnego.

   Ta dokumentacja dotyczy przede wszystkim pierwszy i trzeci kroków procesu. Podczas tych czynności możesz organizować funkcje pakietu VSPackage w WICs, dzięki czemu można ramki Twojej wersji i obsługi strategii do konta w kolejnych wersjach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pozostałe trzy kroki są zostały szczegółowo opisane w dokumentacji tego Instalatora Windows w zestawie SDK platformy.

## <a name="key-terms"></a>Kluczowe terminy
 Poniżej przedstawiono definicjami najważniejszych terminów związanych z technologii Instalatora Windows.

 Pliki zasobów, klucze rejestru, skróty, lub i tak dalej, mogą być zainstalowane na komputerze. Te zasoby są logicznie pogrupowane w składniki Instalatora Windows.

 Instalator Windows component (WIC) podstawowa jednostka instalacji reprezentujący logiczne grupowanie powiązanych zasobów, które są zainstalowane, a następnie odinstalowana jako jednostka. Składniki Instalatora Windows są identyfikowane przez identyfikator unikatowy składnika lub identyfikator GUID. Ponadto Instalator Windows obsługuje jej zliczanie na poziomie WIC. Przechowywanie wersji maksymalnej elastyczności dołączyć nie więcej niż jeden podstawowy zasób, np. biblioteki DLL, WIC danego. Należy pamiętać, że po identyfikacji i wypełnić WIC, nadaj mu identyfikator GUID i wdróż je, nie można zmienić jego skład. Aby uzyskać więcej informacji, zobacz [organizowanie aplikacji do składników](/windows/desktop/Msi/organizing-applications-into-components).

 Jednostka (pakiet Redist) wdrożenia, który składa się z pliku .msi i zewnętrzne pliki źródłowe, do których może wskazywać tego pliku. Pakiet zawiera wszystkie informacje wymagające Instalatora Windows do uruchamiania interfejsu użytkownika i zainstalowania lub odinstalowania aplikacji.

 plik msi magazynu strukturalnego pliku COM, zawierających instrukcje i dane niezbędne do zainstalowania aplikacji. Każdy pakiet zawiera co najmniej jeden plik msi. Plik msi zawiera baza danych Instalatora, strumień informacji podsumowania i prawdopodobnie co najmniej jeden przekształceń i wewnętrzne pliki źródłowe. Pliki do zainstalowania można można skompresowany do pliku cabinet i przechowywane w strumieniu w pliku msi lub przechowywane, skompresowane albo nieskompresowane poza plikiem msi na nośniku źródła. Aby uzyskać więcej informacji, zobacz [rozszerzeń plików Instalatora Windows](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Wymuszanie reguł Instalatora Windows
 Dwa zestawy reguł określają wdrażanie zasobów za pomocą składników z konfiguracją. Jeden zestaw reguł jest obsługiwana przez Instalatora Windows, podczas gdy powinien wymuszać drugiego zestawu jako autor instalacji.

> [!NOTE]
>  Wymuszanie reguł Instalatora Windows występuje tylko wtedy, gdy jest sprawdzana poprawność pliku msi. Niemniej jednak to ostrzeżenie, że traktować te reguły jako najlepsze rozwiązanie. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności instalacji bazy danych](/windows/desktop/Msi/validating-an-installation-database) i [sprawdzanie poprawności pakietu](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Reguły wymuszane przez Instalatora

-   Wszystkie pliki w danym składnika musi być zainstalowany na tym samym katalogu. Z drugiej strony pliki zainstalowane na oddzielnych folderów muszą należeć do rozdzielania składników.

-   Może istnieć tylko jedna ścieżka klucza dla danego składnika. Ścieżka klucza jest po prostu plików lub rejestru klucz, który reprezentuje cały składnik.

#### <a name="component-provider-responsibilities"></a>Obowiązki dostawcy składników

-   Dwa zasoby, które może być udostępniona oddzielnie w kolejnych wersjach powinny istnieć w osobne składniki. Powinny zostać utworzone zasoby do tego samego składnika, tylko wtedy, gdy masz pewność, że te zasoby nigdy nie zostanie udostępniona oddzielnie. W rzeczywistości, zalecane jest, wszystkie podstawowe zasoby (na przykład dll) zawsze znajdują się w oddzielnych WICs. Aby uzyskać więcej informacji, zobacz [Definiowanie składniki Instalatora](/windows/desktop/Msi/defining-installer-components).

-   Brak określonej wersji zasobu nigdy nie powinien wysłać w więcej niż jeden WIC.

## <a name="see-also"></a>Zobacz też
- [Co się stanie, jeśli reguły składników są przerwane?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)