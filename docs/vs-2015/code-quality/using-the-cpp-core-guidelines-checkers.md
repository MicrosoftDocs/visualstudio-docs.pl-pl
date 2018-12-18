---
title: Za pomocą narzędzia do sprawdzania podstawowych wytycznych dotyczących języka C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1153f7a32c26946fafb1230699c4afcae976cd9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799564"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Za pomocą narzędzia do sprawdzania podstawowych wytycznych dotyczących języka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podstawowych wytycznych dotyczących języka C++ są przenośne zbiór wytycznych, reguł i najlepsze rozwiązania dotyczące programowania w języku C++, utworzone przez ekspertów z C++ i projektantów.  Program Visual Studio obsługuje teraz pakiety dodatku, tworzonych dodatkowe reguły dla kodu, narzędziami do analizowania sprawdzać Twój kod pod kątem zgodności z podstawowych wytycznych dotyczących języka C++, a także sugerują ulepszenia.  
  
## <a name="the-c-core-guidelines-project"></a>C++ podstawowych wytycznych dotyczących projektu  
 Utworzone przez Bjarne'a Stroustrupa i innym osobom, podstawowych wytycznych dotyczących języka C++ to przewodnik do wykorzystania nowoczesnym języku C++, bezpiecznie i wydajnie. Wytyczne podkreślić bezpieczeństwa typu statycznego i bezpieczeństwa zasobów. Identyfikowanie sposoby wyeliminowania lub zminimalizować najbardziej podatne na błędy części języka i sugeruje jak sprawić, że kod jest prostszy i wydajniej w niezawodny sposób. Te wytyczne są obsługiwane przez Standard C++ Foundation. Aby dowiedzieć się więcej, zapoznaj się z dokumentacją, [podstawowych wytycznych dotyczących języka C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), a dostęp do plików projektu dokumentacji podstawowych wytycznych dotyczących języka C++ na [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Firma Microsoft obsługuje nakład pracy w podstawowych wytycznych dotyczących języka C++, wprowadzając podstawowe sprawdzanie języka C++ reguł analizy kodu ustawia, czy można dodawać do projektów przy użyciu pakietu Nuget. Pakiet o nazwie Microsoft.CppCoreCheck i jest on dostępny w [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Ten pakiet wymaga, że masz co najmniej zainstalowanego programu Visual Studio 2015 z aktualizacją Update 1.  
  
 Pakiet instaluje też inny pakiet jako zależność, tylko nagłówek wskazówek dotyczących pomocy technicznej biblioteki (GSL). GSL jest również dostępna w witrynie GitHub pod [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Włącz wskazówki podstawowe sprawdzanie języka C++ w analizie kodu  
 Aby włączyć narzędzia analizy kodu podstawowe sprawdzanie języka C++, należy zainstalować pakiet Microsoft.CppCoreCheck NuGet do każdego projektu C++, który chcesz sprawdzić w programie Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Aby dodać pakiet Microsoft.CppCoreCheck do projektu  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe projektu w rozwiązaniu, które chcesz dodać pakiet do. Wybierz **Zarządzaj pakietami NuGet** otworzyć **Menedżera pakietów NuGet**.  
  
2. W **Menedżera pakietów NuGet** okna, wyszukaj Microsoft.CppCoreCheck.  
  
    ![Pokazuje okno Menedżera pakietów Nuget, pakietów CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Wybierz pakiet Microsoft.CppCoreCheck, a następnie wybierz **zainstalować** przycisk, aby dodać reguły do projektu.  
  
   Pakiet NuGet dodaje dodatkowe pliki .targets MSBuild do projektu, która jest wywoływana po włączeniu analizy kodu w projekcie. Ten plik .targets dodaje zasady podstawowe sprawdzanie języka C++ jako dodatkowe rozszerzenia narzędzie do analizy kodu programu Visual Studio.  
  
   Można włączyć analizę kodu projektu, wybierając **Włącz analizę kodu podczas kompilacji** pola wyboru w **analizy kodu** części **stron właściwości** okno dialogowe Projekt.  
  
   ![Strony właściwości dla ustawień ogólnych analizy kodu](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Podstawowe sprawdzanie języka C++ reguły należały do zestawów reguł domyślne, które są uruchamiane po włączeniu analizy kodu. Ponieważ zasady podstawowe sprawdzanie języka C++, są w fazie projektowania, niektóre reguły nie może być gotowa do użycia na cały kod, ale może być informacyjne podczas programowania. Te reguły są wydawane jako eksperymentalne. Możesz wybrać, czy do uruchamiania reguły wydana lub eksperymentalnych we właściwościach projektu.  
  
   ![Strony właściwości dla ustawień rozszerzenia analizy kodu](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Aby włączyć lub wyłączyć zestawy reguł podstawowe sprawdzanie języka C++, otwórz **stron właściwości** okno dialogowe dla Twojego projektu. W obszarze **właściwości konfiguracji**, rozwiń węzeł **analizy kodu**, **rozszerzenia**. W menu rozwijanym obok kontrolować **Włącz podstawowe sprawdzanie języka C++ (wydania)** lub **Włącz podstawowe sprawdzanie języka C++ (funkcja eksperymentalna)**, wybierz **tak** lub **nie**. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Sprawdź typy, granice i okresów istnienia  
 Podstawowe sprawdzanie języka C++ pakiet zawiera obecnie narzędzia do sprawdzania dla [bezpieczeństwo typu](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [granic bezpieczeństwa](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), i [bezpieczeństwa okres istnienia](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) profilów.  
  
 Oto przykład tego rodzaju problemy, które można znaleźć reguły podstawowe sprawdzanie języka C++:  
  
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
  
 W tym przykładzie pokazano kilka ostrzeżeń, które można znaleźć reguły podstawowe sprawdzanie języka C++:  
  
- C26494 jest reguła Type.5: zawsze Inicjuj obiekt.  
  
- C26485 jest reguła Bounds.3: nie zanikania tablicy do wskaźnika.  
  
- C26481 jest reguła Bounds.1: nie używaj arytmetyki wskaźnika. Zamiast nich należy używać słów kluczowych `span`.  
  
  Jeśli zestawów reguł podstawowe sprawdzanie języka C++ analizy kodu są zainstalowane i włączone, skompilować ten kod, pierwsze dwa ostrzeżenia są dane wyjściowe, ale trzecie jest pomijane. Oto dane wyjściowe kompilacji z przykładowego kodu:  
  
  **1 >---Kompilacja została rozpoczęta: Projekt: CoreCheckExample, konfiguracja: Debug Win32 —**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (pełny plik PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): ostrzeżenie C26494: zmienna "AAR" jest uninitializ**  
**wyd zawsze Inicjuj obiekt. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**IDENTYFIKATOR = 620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): ostrzeżenie C26485: wyrażenie "AAR": Brak tablicy do**  
 **decay wskaźnika. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== Kompilacja: 1 zakończyła się pomyślnie, 0 nie, aktualne, 0 0 pominięte ===** podstawowych wytycznych dotyczących języka C++, czy istnieją ułatwia pisanie kodu lepsze i bezpieczniejsze. Jednak w przypadku wystąpienia, gdzie nie należy zastosować regułę lub profil jest łatwy do pomijania go bezpośrednio w kodzie. Możesz użyć `gsl::suppress` atrybutu, aby zapobiec podstawowe sprawdzanie języka C++ wykrywania i raportowania wszelkie naruszenia reguły w następującym fragmencie kodu. Możesz oznaczyć pojedyncze instrukcje, aby pominąć określone zasady. Można nawet pominąć cały profil granic, pisząc `[[gsl::suppress(bounds)]]` bez uwzględniania numer określonej reguły.  
  
## <a name="use-the-guideline-support-library"></a>Korzystanie z biblioteki obsługi wskazówek dotyczących  
 Pakiet Microsoft.CppCoreCheck NuGet instaluje też pakiet zawierający implementację firmy Microsoft z biblioteki obsługi wskazówek dotyczących (GSL). GSL jest również dostępna w formie autonomicznej na [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Ta biblioteka jest przydatne, jeśli chcesz obserwować podstawowych wytycznych dotyczących. GSL zawiera definicje, które umożliwiają Zamień podatne konstrukcje bezpieczniejszych alternatyw. Na przykład, możesz zastąpić `T*, length` pary parametrów za pomocą `span<T>` typu. GSL jest typu open source, więc jeśli chcesz Przyjrzyj się źródeł biblioteki, dodać komentarz lub współtworzyć, projekt można znaleźć w folderze [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).



