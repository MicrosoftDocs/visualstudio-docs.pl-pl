---
title: Instalator Windows podstawowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4693654e12dc37209cb92e3e2ba95bde8bd13e77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687676"
---
# <a name="windows-installer-basics"></a>Podstawowe informacje dotyczące Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Instalator Windows instaluje i odinstalowuje aplikacje lub oprogramowanie na komputerze użytkownika, wykonując te zadania w jednostkach o nazwie składniki Instalator Windows (czasami nazywane WICs lub tylko składnikami). Identyfikator GUID identyfikuje każdy WIC, który jest podstawową jednostką instalacji i zliczania odwołań dla Instalatora przy użyciu Instalator Windows.  
  
 Aby uzyskać pełną dokumentację Instalator Windows, zobacz temat zestaw SDK platformy, [Instalator Windows](/previous-versions/2kt85ked(v=vs.120)).  
  
## <a name="authoring-a-vspackage"></a>Tworzenie elementu pakietu VSPackage  
 Instalator Windows używa pakietów instalacyjnych, które zawierają informacje, które Instalator Windows muszą zainstalować, odinstalować lub naprawić produkt i uruchomić interfejs użytkownika Instalatora (UI). Każdy pakiet instalacyjny zawiera plik msi, który zawiera bazę danych instalacji, strumień informacji podsumowujących i strumienie danych dla różnych części instalacji. Aby skorzystać z Instalatora, należy utworzyć instalację. Ponieważ Instalator organizuje instalacje wokół koncepcji składników i zapisuje informacje o instalacji w relacyjnej bazie danych, proces tworzenia pakietu instalacyjnego w szerokim zakresie obejmuje następujące kroki:  
  
1. Zaplanuj Tworzenie instalacji w celu obsługi wersji i strategii Side-by-side.  
  
2. Zidentyfikuj funkcje, które mają być prezentowane użytkownikom.  
  
3. Organizuj pakietu VSPackage i zależności w składniki.  
  
4. Wypełnij bazę danych instalacji informacjami.  
  
5. Sprawdź poprawność pakietu instalacyjnego.  
  
   Ta dokumentacja dotyczy przede wszystkim pierwszego i trzeciego kroku procesu. Podczas wykonywania tych kroków możesz zorganizować funkcje pakietu VSPackage w WICs, aby można było umieścić strategię przechowywania wersji i obsługi, aby uwzględnić kolejne wersje programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pozostałe trzy kroki zostały szczegółowo omówione w dokumentacji Instalator Windows w zestawie SDK platformy.  
  
## <a name="key-terms"></a>Najważniejsze terminy  
 Poniżej przedstawiono definicje najważniejszych terminów związanych z technologią Instalator Windows.  
  
 Zasób  
 Pliki, klucze rejestru, skróty lub i tak dalej, które mogą być zainstalowane na komputerze. Te zasoby są grupowane logicznie w składniki Instalator Windows.  
  
 Składnik Instalator Windows (WIC)  
 Podstawowa jednostka instalacji reprezentująca logiczne grupowanie powiązanych zasobów, które są instalowane i odinstalowywane jako jednostka. Składniki Instalator Windows są identyfikowane za pomocą unikatowego identyfikatora składnika lub identyfikatora GUID. Ponadto Instalator Windows utrzymuje zliczanie odwołań na poziomie WIC. Aby zapewnić maksymalną elastyczność wersji, należy uwzględnić w danym WIC nie więcej niż jeden zasób podstawowy, taki jak DLL. Zwróć uwagę, że po określeniu i wypełnieniu elementu WIC nadaj mu identyfikator GUID i Wdróż go, ale nie możesz zmienić jego kompozycji. Aby uzyskać więcej informacji, zobacz [organizowanie aplikacji do składników](https://msdn.microsoft.com/library/aa370561.aspx)programu.  
  
 Pakiet (pakiet Redist)  
 Jednostka wdrożenia, która składa się z pliku MSI i zewnętrznych plików źródłowych, do których ten plik może wskazywać. Pakiet zawiera wszystkie informacje, które Instalator Windows muszą uruchamiać interfejs użytkownika oraz instalować lub odinstalowywać aplikację.  
  
 Plik msi  
 Plik magazynu strukturalnego COM zawierający instrukcje i dane wymagane do zainstalowania aplikacji. Każdy pakiet zawiera co najmniej jeden plik msi. Plik. msi zawiera bazę danych Instalatora, strumień informacji podsumowujących i prawdopodobnie co najmniej jedną transformacje i wewnętrzne pliki źródłowe. Pliki, które mają zostać zainstalowane, mogą być kompresowane do pliku cabinet i przechowywane w strumieniu na dysku. msi lub przechowywane, kompresowane lub nieskompresowane, poza plikiem MSI na nośniku źródłowym. Aby uzyskać więcej informacji, zobacz [rozszerzenia plików Instalator Windows](https://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Wymuszanie reguł Instalator Windows  
 Dwa zestawy reguł określają wdrażanie zasobów za pomocą składników Instalatora. Jeden zestaw reguł jest obsługiwany przez Instalator Windows samego, podczas gdy należy wymusić drugi zestaw jako autora instalacji.  
  
> [!NOTE]
> Wymuszanie reguł Instalator Windows występuje tylko wtedy, gdy uruchomisz weryfikację pliku msi. Jednak należy zachować ostrożność traktowania tych reguł zgodnie z najlepszymi rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Walidacja bazy danych instalacji](https://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) i [Walidacja pakietu](https://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Zasady wymuszane przez Instalatora  
  
- Wszystkie pliki w danym składniku muszą być zainstalowane w tym samym katalogu. Z drugiej strony pliki zainstalowane w oddzielnych folderach muszą należeć do osobnych składników.  
  
- Dla każdego składnika może istnieć tylko jedna ścieżka klucza. Ścieżka klucza to po prostu plik lub klucz rejestru reprezentujący cały składnik.  
  
#### <a name="component-provider-responsibilities"></a>Obowiązki dostawcy składników  
  
- Wszystkie dwa zasoby, które mogą być dostarczane osobno w kolejnych wersjach, powinny znajdować się w oddzielnych składnikach. Zasoby powinny być pogrupowane w ten sam składnik tylko wtedy, gdy masz pewność, że te zasoby nigdy nie będą dostarczane osobno. W rzeczywistości zaleca się, aby wszystkie podstawowe zasoby (na przykład dll) zawsze istniały w oddzielnych WICs. Aby uzyskać więcej informacji, zobacz [Definiowanie składników Instalatora](https://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
- Żaden zasób z wersjami powinien być kiedykolwiek dostarczany w więcej niż jednym WIC.  
  
## <a name="see-also"></a>Zobacz też  
 [Co się stanie w przypadku przerwania reguł składników?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)
