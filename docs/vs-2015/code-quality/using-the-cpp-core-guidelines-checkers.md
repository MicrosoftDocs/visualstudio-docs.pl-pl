---
title: Korzystanie z C++ funkcji sprawdzania podstawowych wytycznych | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ccc44b77c4524e7d707ce3fe407d204d729017ff
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291247"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Podstawowe wytyczne są przenośnym zestawem wytycznych, zasad i najlepszych rozwiązań dotyczących kodowania C++ utworzonego przez C++ ekspertów i projektantów.  Program Visual Studio obsługuje teraz pakiety dodatków, które tworzą dodatkowe reguły dla narzędzi do analizy kodu, aby sprawdzić zgodność kodu z C++ podstawowymi wskazówkami i zasugerować ulepszenia.  
  
## <a name="the-c-core-guidelines-project"></a>Projekt C++ podstawowych wytycznych  
 Podstawowe wytyczne są tworzone przez Bjarne'a Stroustrupa i C++ inne, ale w sposób C++ bezpieczny i efektywny. Wytyczne podkreślają bezpieczeństwo typu statycznego i bezpieczeństwo zasobów. Identyfikują one sposoby eliminacji lub minimalizowania najbardziej podatnych na błędy części języka, a także sugerują sposób prostszego i bardziej wydajnego wykonywania kodu. Te wytyczne są obsługiwane przez standardową C++ podstawę. Aby dowiedzieć się więcej, zobacz dokumentację, [ C++ podstawowe wytyczne](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)i dostęp do C++ plików projektu dokumentacji podstawowych wytycznych w serwisie [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Firma Microsoft obsługuje C++ podstawowe wytyczne, wprowadzając C++ podstawowe zestawy reguł analizy kodu, które można dodać do projektów za pomocą pakietu NuGet. Pakiet ma nazwę Microsoft. CppCoreCheck i jest dostępny w [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Ten pakiet wymaga co najmniej programu Visual Studio 2015 z aktualizacją Update 1.  
  
 Pakiet instaluje również inny pakiet jako zależność, tylko w przypadku podstawowej biblioteki obsługi (GSL). GSL jest również dostępna w witrynie GitHub w [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Włącz C++ podstawowe wskazówki dotyczące sprawdzania w analizie kodu  
 Aby włączyć C++ podstawowe narzędzia do analizy kodu, zainstaluj pakiet NuGet Microsoft. CppCoreCheck w każdym C++ projekcie, który chcesz sprawdzić w programie Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Aby dodać pakiet Microsoft. CppCoreCheck do projektu  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe projektu w rozwiązaniu, do którego chcesz dodać pakiet. Wybierz pozycję **Zarządzaj pakietami NuGet** , aby otworzyć **Menedżera pakietów NuGet**.  
  
2. W oknie **Menedżer pakietów NuGet** Wyszukaj ciąg Microsoft. CppCoreCheck.  
  
    ![Okno Menedżera pakietów NuGet zawiera pakiet CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Wybierz pakiet Microsoft. CppCoreCheck, a następnie wybierz przycisk **Instaluj** , aby dodać reguły do projektu.  
  
   Pakiet NuGet dodaje do projektu dodatkowy plik MSBuild. targets, który jest wywoływany po włączeniu analizy kodu dla projektu. Ten plik targets dodaje C++ podstawowe reguły sprawdzania jako dodatkowe rozszerzenie narzędzia do analizy kodu programu Visual Studio.  
  
   Możesz włączyć analizę kodu w projekcie, zaznaczając pole wyboru **Włącz analizę kodu podczas kompilacji** w sekcji **Analiza kodu** okna dialogowego **strony właściwości** dla projektu.  
  
   ![Strona właściwości dla ustawień ogólnych analizy kodu](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Podstawowe reguły sprawdzania stają się częścią domyślnych zestawów reguł, które są uruchamiane po włączeniu analizy kodu. Ponieważ C++ podstawowe reguły sprawdzania są opracowywane, niektóre reguły mogą nie być gotowe do użycia na całym kodzie, ale mogą być niezgodne podczas opracowywania. Te reguły są udostępniane jako eksperymentalne. Możesz wybrać, czy mają być uruchamiane reguły wydane lub eksperymentalne we właściwościach projektu.  
  
   ![Strona właściwości dla ustawień rozszerzeń analizy kodu](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Aby włączyć lub wyłączyć zestawy C++ reguł sprawdzania podstawowe, Otwórz okno dialogowe **strony właściwości** dla projektu. W obszarze **Właściwości konfiguracji**rozwiń węzeł **Analiza kodu**, **rozszerzenia**. W kontrolce listy rozwijanej **obok C++ pozycji Włącz sprawdzanie podstawowe (wydano)** lub **Włącz C++ sprawdzanie podstawowe (eksperymentalne)** wybierz opcję **tak** lub **nie**. Wybierz **przycisk OK** lub **Zastosuj** , aby zapisać zmiany.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Sprawdzanie typów, granic i okresów istnienia  
 Pakiet C++ sprawdzania rdzenia obecnie zawiera składniki sprawdzające [bezpieczeństwo typu](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [bezpieczeństwo granic](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)i profile [bezpieczeństwa okresu istnienia](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Oto przykład rodzaju problemów, które mogą znaleźć C++ podstawowe reguły sprawdzania:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 Ten przykład ilustruje kilka ostrzeżeń, które mogą znaleźć C++ podstawowe reguły sprawdzania:  
  
- C26494 jest typem reguły. 5: zawsze Inicjuj obiekt.  
  
- C26485 jest zakresem reguł. 3: brak zanikania tablicy do wskaźnika.  
  
- C26481 jest zakresem reguł. 1: nie używaj arytmetyki wskaźnika. Zamiast nich należy używać słów kluczowych `span`.  
  
  Jeśli C++ podstawowe zestaw reguł analizy kodu są instalowane i włączane podczas kompilowania tego kodu, pierwsze dwa ostrzeżenia są wyjściowe, ale trzeci jest pomijany. Oto dane wyjściowe kompilacji z przykładowego kodu:  
  
**1 > kompilacja------rozpoczęta: projekt: CoreCheckExample, konfiguracja: Debug Win32--**  
**----**  
**1 > CoreCheckExample. cpp**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (pełny plik PDB)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): ostrzeżenie C26494: zmienna "ARR" jest uninitializ**  
**Ed. zawsze Inicjuj obiekt. (Type. 5: https://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): ostrzeżenie C26485: wyrażenie "ARR": brak tablicy do**  
**zanik wskaźnika. (bounds. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = = **Kompilacja: 1 zakończono pomyślnie, 0 nie powiodło się, 0 aktualne, 0 pominięte =** = = = = = = = = C++ Podstawowe wskazówki ułatwiają pisanie lepszych i bezpieczniejszych kodów. Jeśli jednak istnieje wystąpienie, w którym nie należy stosować reguły lub profilu, można je łatwo pominąć bezpośrednio w kodzie. Można użyć atrybutu `gsl::suppress`, aby zachować C++ podstawowe sprawdzenie w wykrywaniu i raportowaniu naruszeń reguły w poniższym bloku kodu. Można oznaczyć poszczególne instrukcje, aby pominąć określone reguły. Można nawet pominąć profil całego ograniczenia, pisząc `[[gsl::suppress(bounds)]]` bez uwzględniania określonego numeru reguły.  
  
## <a name="use-the-guideline-support-library"></a>Korzystanie z biblioteki podstawowej pomocy technicznej  
 Pakiet NuGet Microsoft. CppCoreCheck instaluje również pakiet zawierający implementację podstawowej biblioteki pomocy technicznej firmy Microsoft (GSL). GSL jest również dostępna w autonomicznej formie w [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). Ta biblioteka jest przydatna, jeśli chcesz postępować zgodnie z podstawowymi wskazówkami. GSL zawiera definicje, które umożliwiają zamianę konstrukcji podatnych na błędy z bezpieczniejszymi alternatywami. Na przykład można zastąpić `T*, length` parę parametrów `span<T>` typem. GSL jest typu open source, więc jeśli chcesz zapoznać się ze źródłami biblioteki, komentarzem lub współautorem, projekt można znaleźć w [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).
