---
title: Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c7854e982a369816a9dac2c54df48e98ec6d3b7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804237"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Rozwiązywanie problemów z błędami obiektów docelowych programu .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
W tym temacie opisano błędy programu MSBuild, które mogą wystąpić z powodu odwołania problemy i jak można naprawić te błędy.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Ma odwołanie do projektu lub zestawu, który jest przeznaczony dla innej wersji programu .NET Framework  
 Możesz tworzyć aplikacje odwołujące się do projektów lub zestawów, przeznaczonych dla różnych wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Na przykład utworzysz aplikację, który jest przeznaczony dla profilu klienta dla [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , ale odwołuje się do zestawu, który jest przeznaczony dla .NET Framework 2.0. Jednak jeśli tworzysz projekt, który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], nie można ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla profilu klienta dla [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] sam. Aby naprawić błąd, upewnij się, że aplikacja jest przeznaczony dla profil lub profile, które są zgodne z profilem, który jest określony przez projektów lub zestawów, do których odwołuje się do aplikacji.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Jest ponownie skierowany projektu do innej wersji programu .NET Framework  
 Jeśli zmienisz wersję docelową [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dla aplikacji, Visual Studio zmieniają niektóre odwołania, ale musisz ręcznie zaktualizować niektóre odwołania. Na przykład jeden z wymienionych wcześniej błędów może wystąpić, jeśli zmienisz aplikację docelową [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] i że aplikacja ma zasoby lub ustawień, które opierają się na profil klienta [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)].  
  
 Aby obejść ustawienia aplikacji, otwórz **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki**, a następnie edytuj plik app.config, w edytorze XML programu Visual Studio. Zmień wersję w ustawieniach, aby dopasować odpowiednią wersję programu .NET Framework. Na przykład można zmienić ustawienie wersji z 4.0.0.0, aby 2.0.0.0 lub nowszej. Podobnie, dla aplikacji, która została dodana zasobów, należy otworzyć **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** , rozwiń pozycję **mój projekt** (Visual Basic) lub **Właściwości** (C#), a następnie edytuj plik Resources.resx w edytorze XML programu Visual Studio. Zmień ustawienie wersji z 4.0.0.0 na 2.0.0.0 lub nowszej.  
  
 Jeśli aplikacja ma zasoby, takie jak ikony lub mapy bitowe lub ustawienia, takie jak parametry połączenia danych, można również rozwiązać błąd, usuwając wszystkie elementy na **ustawienia** stronie **projektanta projektu**, a następnie ponowne dodanie wymaganych ustawień.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Projekt do innej wersji programu .NET Framework jest ponownie skierowany i odwołania nie został rozwiązany  
 Jeśli przekierowanie projektu do innej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], odwołaniami mogą nie być rozpoznawane prawidłowo w niektórych przypadkach. Jawne w pełni kwalifikowanego odwołania do zestawów często przyczyną tego problemu, ale można go naprawić przez usunięcie odwołania, które nie umożliwiają rozwiązania, a następnie dodanie ich do projektu. Alternatywnie można edytować plik projektu w celu zastąpienia odwołań. Najpierw należy usunąć odwołania następującą postać:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Następnie należy zastąpić je prostego formularza:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Po zamknięciu i ponownym otwarciu projektu powinien również można odbudować ją, aby zapewnić poprawnie rozpoznać wszystkie odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Przeznaczone dla określonej wersji platformy .NET](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Wielowersyjność kodu](../msbuild/msbuild-multitargeting-overview.md)
