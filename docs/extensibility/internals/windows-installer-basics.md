---
title: Instalator Windows podstawowe | Microsoft Docs
description: Dowiedz się więcej na temat Instalator Windows do użycia podczas instalowania pakietu VSPackage, w tym organizowania funkcji pakietu VSPackage w składniki Instalator Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4081c79b7492e369e19187a099bf975275cb371c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869495"
---
# <a name="windows-installer-basics"></a>Podstawowe informacje dotyczące Instalatora Windows
Instalator Windows instaluje i odinstalowuje aplikacje lub oprogramowanie na komputerze użytkownika, wykonując te zadania w jednostkach o nazwie składniki Instalator Windows (czasami nazywane WICs lub tylko składnikami). Identyfikator GUID identyfikuje każdy WIC, który jest podstawową jednostką instalacji i zliczania odwołań dla Instalatora przy użyciu Instalator Windows.

 Aby uzyskać pełną dokumentację Instalator Windows, zobacz temat zestaw SDK platformy, [Instalator Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Tworzenie elementu pakietu VSPackage
 Instalator Windows używa pakietów instalacyjnych, które zawierają informacje, które Instalator Windows muszą zainstalować, odinstalować lub naprawić produkt i uruchomić interfejs użytkownika Instalatora (UI). Każdy pakiet instalacyjny zawiera plik msi, który zawiera bazę danych instalacji, strumień informacji podsumowujących i strumienie danych dla różnych części instalacji. Aby skorzystać z Instalatora, należy utworzyć instalację. Ponieważ Instalator organizuje instalacje wokół koncepcji składników i zapisuje informacje o instalacji w relacyjnej bazie danych, proces tworzenia pakietu instalacyjnego w szerokim zakresie obejmuje następujące kroki:

1. Zaplanuj Tworzenie instalacji w celu obsługi wersji i strategii Side-by-side.

2. Zidentyfikuj funkcje, które mają być prezentowane użytkownikom.

3. Organizuj pakietu VSPackage i zależności w składniki.

4. Wypełnij bazę danych instalacji informacjami.

5. Sprawdź poprawność pakietu instalacyjnego.

   Ta dokumentacja dotyczy przede wszystkim pierwszego i trzeciego kroku procesu. Podczas wykonywania tych kroków możesz zorganizować funkcje pakietu VSPackage w WICs, aby można było umieścić strategię przechowywania wersji i obsługi, aby uwzględnić kolejne wersje programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Pozostałe trzy kroki zostały szczegółowo omówione w dokumentacji Instalator Windows w zestawie SDK platformy.

## <a name="key-terms"></a>Najważniejsze terminy
 Poniżej przedstawiono definicje najważniejszych terminów związanych z technologią Instalator Windows.

 Pliki zasobów, klucze rejestru, skróty lub i tak dalej, które mogą być zainstalowane na komputerze. Te zasoby są grupowane logicznie w składniki Instalator Windows.

 Składnik Instalator Windows (WIC) podstawowa jednostka instalacji reprezentująca logiczne grupowanie powiązanych zasobów, które są instalowane i odinstalowywane jako jednostka. Składniki Instalator Windows są identyfikowane za pomocą unikatowego identyfikatora składnika lub identyfikatora GUID. Ponadto Instalator Windows utrzymuje zliczanie odwołań na poziomie WIC. Aby zapewnić maksymalną elastyczność wersji, należy uwzględnić w danym WIC nie więcej niż jeden zasób podstawowy, taki jak DLL. Zwróć uwagę, że po określeniu i wypełnieniu elementu WIC nadaj mu identyfikator GUID i Wdróż go, ale nie możesz zmienić jego kompozycji. Aby uzyskać więcej informacji, zobacz [organizowanie aplikacji do składników](/windows/desktop/Msi/organizing-applications-into-components)programu.

 Pakiet (pakiet Redist) jednostka wdrożenia, która składa się z pliku MSI i zewnętrznych plików źródłowych, do których ten plik może wskazywać. Pakiet zawiera wszystkie informacje, które Instalator Windows muszą uruchamiać interfejs użytkownika oraz instalować lub odinstalowywać aplikację.

 Plik MSI plik magazynu strukturalnego COM zawierający instrukcje i dane wymagane do zainstalowania aplikacji. Każdy pakiet zawiera co najmniej jeden plik msi. Plik. msi zawiera bazę danych Instalatora, strumień informacji podsumowujących i prawdopodobnie co najmniej jedną transformacje i wewnętrzne pliki źródłowe. Pliki, które mają zostać zainstalowane, mogą być kompresowane do pliku cabinet i przechowywane w strumieniu na dysku. msi lub przechowywane, kompresowane lub nieskompresowane, poza plikiem MSI na nośniku źródłowym. Aby uzyskać więcej informacji, zobacz [rozszerzenia plików Instalator Windows](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Wymuszanie reguł Instalator Windows
 Dwa zestawy reguł określają wdrażanie zasobów za pomocą składników Instalatora. Jeden zestaw reguł jest obsługiwany przez Instalator Windows samego, podczas gdy należy wymusić drugi zestaw jako autora instalacji.

> [!NOTE]
> Wymuszanie reguł Instalator Windows występuje tylko wtedy, gdy uruchomisz weryfikację pliku msi. Jednak należy zachować ostrożność traktowania tych reguł zgodnie z najlepszymi rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Walidacja bazy danych instalacji](/windows/desktop/Msi/validating-an-installation-database) i [Walidacja pakietu](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Reguły Installer-Enforced

- Wszystkie pliki w danym składniku muszą być zainstalowane w tym samym katalogu. Z drugiej strony pliki zainstalowane w oddzielnych folderach muszą należeć do osobnych składników.

- Dla każdego składnika może istnieć tylko jedna ścieżka klucza. Ścieżka klucza to po prostu plik lub klucz rejestru reprezentujący cały składnik.

#### <a name="component-provider-responsibilities"></a>Component-Provider obowiązki

- Wszystkie dwa zasoby, które mogą być dostarczane osobno w kolejnych wersjach, powinny znajdować się w oddzielnych składnikach. Zasoby powinny być pogrupowane w ten sam składnik tylko wtedy, gdy masz pewność, że te zasoby nigdy nie będą dostarczane osobno. W rzeczywistości zaleca się, aby wszystkie podstawowe zasoby (na przykład dll) zawsze istniały w oddzielnych WICs. Aby uzyskać więcej informacji, zobacz [Definiowanie składników Instalatora](/windows/desktop/Msi/defining-installer-components).

- Żaden zasób z wersjami powinien być kiedykolwiek dostarczany w więcej niż jednym WIC.

## <a name="see-also"></a>Zobacz też
- [Co się stanie w przypadku przerwania reguł składników?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
