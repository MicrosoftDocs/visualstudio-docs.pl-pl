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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a816981b41dd8ca2a2119bbd99c776c6a7e2436
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296883"
---
# <a name="visual-studio-multi-targeting-overview"></a>Wielowersyjność kodu Visual Studio ― Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]można określić wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], która jest wymagana dla aplikacji. W związku z tym, jeśli chcesz użyć tej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby kontynuować tworzenie projektu, który został uruchomiony w starszej wersji, nie musisz zmieniać elementu docelowego struktury. Można również utworzyć rozwiązania zawierającego projekty tego kierują do różnych wersji Framework. Adresowanie pozwala zagwarantować, że aplikacja używa tylko te funkcje, które są dostępne w określonej wersji Framework.

> [!TIP]
> Można również przeznaczać aplikacje dla różnych platform. Aby uzyskać więcej informacji, zobacz wiele [obiektów docelowych](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Funkcji określania wartości docelowej Framework
 Adresowanie obejmuje następujące funkcje:

- Po otwarciu projektu, który jest przeznaczony dla starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] można go automatycznie uaktualnić lub pozostawić obiekt docelowy jako.

- Podczas tworzenia projektu można określić wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], która ma być docelowa.

- Można zmienić wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], do której należy istniejący projekt.

- W każdym z kilku projektów w tym samym rozwiązaniu można wskazać inną wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

- W przypadku zmiany wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], do której odwołuje się projekt, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] wprowadza wszelkie wymagane zmiany dotyczące odwołań i plików konfiguracyjnych.

  Podczas pracy nad projektem, który jest przeznaczony dla starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], program Visual Studio dynamicznie zmienia środowisko programistyczne w następujący sposób:

- Filtruje elementy w oknie dialogowym **Nowy projekt** , okno dialogowe **Dodaj nowy element** , okno dialogowe **Dodaj nowe odwołanie** i okno dialogowe **Dodaj odwołanie do usługi** , aby pominąć opcje, które nie są dostępne w wersji dostosowanej.

- Filtruje niestandardowe kontrolki w **przyborniku** , aby usunąć te, które nie są dostępne w wersji dostosowanej, i wyświetlić tylko najbardziej aktualne kontrolki, gdy dostępnych jest wiele kontrolek.

- Filtruje IntelliSense, aby pominąć funkcje językowe, które nie są dostępne w wersji docelowej.

- Filtruje właściwości w oknie **Właściwości** , aby pominąć te, które nie są dostępne w wersji dostosowanej.

- Filtruje opcje menu, aby pominąć opcje, które nie są dostępne w wersji docelowej.

- W przypadku kompilacji wykorzystuje wersję kompilatora i opcje kompilatora, które są odpowiednie dla wersji docelowej.

> [!NOTE]
> Adresowanie nie gwarantuje, że Twoja aplikacja będzie działać poprawnie. Należy przetestować aplikację w taki sposób, aby upewnić się, że jest uruchamiana w wersji docelowej. Nie można wskazywać wersji struktury, które są starsze niż .NET Framework 2.0.

## <a name="selecting-a-target-framework-version"></a>Wybieranie wersji platformy docelowej
 Podczas tworzenia projektu, w oknie dialogowym **Nowy projekt** wybierz docelową wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Lista dostępnych szablonów projektów zostanie odfiltrowana według wyboru. W istniejącym projekcie można zmienić wersję docelową [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] w oknie dialogowym właściwości projektu. Aby uzyskać więcej informacji, zobacz [How to: Target of a wersja .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
> W wersjach Express programu Visual Studio nie można ustawić platformy docelowej w oknie dialogowym **Nowy projekt** .

## <a name="resolving-system-and-user-assembly-references"></a>System rozpoznawania i odwołania do zestawów użytkownika
 Aby skierować je do wersji programu .NET Framework, należy najpierw zainstalować odpowiednie odwołania do zestawów. Odwołania do zestawów dla .NET Framework wersje 2,0, 3,0 i 3,5 są zawarte w .NET Framework 3,5 z dodatkiem SP1, które można pobrać z [Centrum pobierania Microsoft, Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) witryny sieci Web. Odwołania do zestawów dla profilu klienta .NET Framework 3,5, .NET Framework 4, profilu klienta .NET Framework 4 i programu Silverlight są również dostępne w witrynie internetowej [pobierania programu Visual Studio](https://go.microsoft.com/fwlink/?LinkId=179687) .

> [!NOTE]
> Profil klienta .NET Framework jest podzbiorem .NET Framework, która zapewnia ograniczony zestaw funkcji i bibliotek. Aby uzyskać więcej informacji o profilach klientów, zobacz [.NET Framework profilu klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 Okno dialogowe **Dodawanie odwołania** wyłącza Zestawy systemowe, które nie odnoszą się do docelowej [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji, tak że nie można ich dodać do projektu przypadkowo. (Zestawy systemowe to pliki dll, które znajdują się w wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]ej). Odwołania należące do wersji platformy, która jest nowsza niż wersja domowa, nie zostaną rozpoznane i nie można dodać kontrolek, które zależą od tego odwołania. Jeśli chcesz włączyć takie odwołanie, zresetuj element docelowy [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] projektu na taki, który zawiera odwołanie.  Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Aby uzyskać więcej informacji na temat odwołań do zestawów, zobacz [rozpoznawanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Włączanie funkcjonalności LINQ
 Kiedy środowiskiem docelowym .NET Framework 3.5 lub nowszy, odniesienie do System.Core i importu poziomu projektu dla System.Linq (tylko w Visual Basic) są dodawane automatycznie. Jeśli chcesz korzystać z funkcji LINQ, użytkownik musi również włączyć opcję wnioskowania (tylko w Visual Basic). Odwołanie i import są usuwane automatycznie, jeśli zmienisz element docelowy do wcześniejszej wersji systemu .NET Framework. Aby uzyskać więcej informacji, zobacz [How to: Create a LINQ Project](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Zobacz też
[Wieloukierunkowane](../msbuild/msbuild-multitargeting-overview.md)
[.NET Framework wiele elementów docelowych dla projektów sieci Web ASP.NET](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)
[zgodność platformy i wymagania systemowe](/visualstudio/productinfo/vs2015-compatibility-vs)
