---
title: Przegląd Wielowersyjności kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a0964e390455b2225ec35debe79cdc79c38ed931
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194564"
---
# <a name="visual-studio-multi-targeting-overview"></a>Wielowersyjność kodu Visual Studio ― Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], można określić wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] jest wymagane dla danej aplikacji. W związku z tym jeśli chcesz używać tej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do dalszego opracowywania projektu rozpoczętego w starszej wersji, nie należy zmieniać celu struktury. Można również utworzyć rozwiązania zawierającego projekty tego kierują do różnych wersji Framework. Adresowanie pozwala zagwarantować, że aplikacja używa tylko te funkcje, które są dostępne w określonej wersji Framework.

> [!TIP]
>  Można również przeznaczać aplikacje dla różnych platform. Aby uzyskać więcej informacji, zobacz [wielowersyjności kodu w programie](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Funkcji określania wartości docelowej Framework
 Adresowanie obejmuje następujące funkcje:

- Po otwarciu projektu, który jest przeznaczony dla starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] może automatycznie go uaktualnić lub pozostawić obiekt docelowy jest.

- Podczas tworzenia projektu można określić wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , ma pod kątem.

- Można zmienić wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] element docelowy, istniejącego projektu.

- Można odwoływać się do różnych wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] w każdym z kilku projektów w tym samym rozwiązaniu.

- Po zmianie wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , projekt jest ukierunkowany [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] wprowadza wszelkie wymagane zmiany dotyczące odwołań i plików konfiguracji.

  Podczas pracy nad projektem, który jest przeznaczony dla starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], Visual Studio dynamicznie zmienia środowisko programistyczne, w następujący sposób:

- Filtruje elementy w **nowy projekt** okno dialogowe **Dodaj nowy element** okno dialogowe **Dodaj nowe odwołanie** okno dialogowe i **Dodaj odwołanie do usługi** okno dialogowe, aby pominąć wybory, które nie są dostępne w wersji docelowej.

- Filtruje niestandardowe formanty w **przybornika** Aby usunąć te, które nie są dostępne w wersji docelowej i pokazać tylko najbardziej aktualne formanty, gdy będzie dostępnych jest kilka formantów.

- Filtruje IntelliSense, aby pominąć funkcje językowe, które nie są dostępne w wersji docelowej.

- Filtruje właściwości w **właściwości** okna, aby pominąć te, które nie są dostępne w wersji docelowej.

- Filtruje opcje menu, aby pominąć opcje, które nie są dostępne w wersji docelowej.

- W przypadku kompilacji wykorzystuje wersję kompilatora i opcje kompilatora, które są odpowiednie dla wersji docelowej.

> [!NOTE]
>  Adresowanie nie gwarantuje, że Twoja aplikacja będzie działać poprawnie. Należy przetestować aplikację w taki sposób, aby upewnić się, że jest uruchamiana w wersji docelowej. Nie można wskazywać wersji struktury, które są starsze niż .NET Framework 2.0.

## <a name="selecting-a-target-framework-version"></a>Wybieranie wersji platformy docelowej
 Podczas tworzenia projektu wybierz docelową [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersja **nowy projekt** okno dialogowe. Lista dostępnych szablonów projektów zostanie odfiltrowana według wyboru. W istniejącym projekcie można zmienić docelową [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji w oknie dialogowym właściwości projektu. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
>  W wersjach Express programu Visual Studio, nie można ustawić platformę docelową **nowy projekt** okno dialogowe.

## <a name="resolving-system-and-user-assembly-references"></a>System rozpoznawania i odwołania do zestawów użytkownika
 Aby skierować je do wersji programu .NET Framework, należy najpierw zainstalować odpowiednie odwołania do zestawów. Odwołania do zestawów dla .NET Framework w wersji 2.0, 3.0 i 3.5 są zawarte w .NET Framework 3.5 SP1, który można pobrać z [Microsoft Download Center, programu Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) witryny sieci Web. Odwołania do zestawów dla .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile i Silverlight są również dostępne [pobieranie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687) witryny sieci Web.

> [!NOTE]
>  Profil klienta .NET Framework jest podzbiorem .NET Framework, która zapewnia ograniczony zestaw funkcji i bibliotek. Aby uzyskać więcej informacji na temat profili klientów, zobacz [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 **Dodaj odwołanie** okno dialogowe wyłącza zestawy systemowe, które nie odnoszą się do obiektu docelowego [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji, aby nie można ich dodać do projektu przypadkowo. (Zestawy systemowe to pliki .dll, które są objęte [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji.) Odwołania, które należą do wersji szablonu, która jest nowsza niż wersja docelowa nie zostanie rozwiązany, a nie można dodać formanty, które są zależne od takiego odwołania. Jeśli chcesz włączyć takie odwołanie, zresetuj [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] obiekcie docelowym projektu na taki, który zawiera odwołanie.  Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Aby uzyskać więcej informacji na temat odwołań do zestawów, zobacz [rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Włączanie funkcjonalności LINQ
 Kiedy środowiskiem docelowym .NET Framework 3.5 lub nowszy, odniesienie do System.Core i importu poziomu projektu dla System.Linq (tylko w Visual Basic) są dodawane automatycznie. Jeśli chcesz korzystać z funkcji LINQ, użytkownik musi również włączyć opcję wnioskowania (tylko w Visual Basic). Odwołanie i import są usuwane automatycznie, jeśli zmienisz element docelowy do wcześniejszej wersji systemu .NET Framework. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu LINQ](http://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Zobacz też
[Wielowersyjność](../msbuild/msbuild-multitargeting-overview.md)
[.NET Framework Wielowersyjność kodu dla projektów sieci Web platformy ASP.NET](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)
[wymagań dotyczących zgodności i systemu platformy](/visualstudio/productinfo/vs2015-compatibility-vs)
