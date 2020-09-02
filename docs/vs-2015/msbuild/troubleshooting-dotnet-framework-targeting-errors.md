---
title: Rozwiązywanie problemów dotyczących błędów .NET Framework Microsoft Docs
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
ms.openlocfilehash: ae55e34f929acca6c708dfc39477f3bd6546f53f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703784"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Rozwiązywanie problemów z błędami obiektów docelowych programu .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano błędy programu MSBuild, które mogą wystąpić z powodu problemów z odwołaniami i sposobu ich rozwiązywania.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odwołuje się do projektu lub zestawu, który jest przeznaczony dla innej wersji .NET Framework  
 Można tworzyć aplikacje odwołujące się do projektów lub zestawów przeznaczonych dla różnych wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Na przykład można utworzyć aplikację, która jest przeznaczona dla profilu klienta dla programu, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ale odwołuje się do zestawu, który jest przeznaczony dla .NET Framework 2,0. Jeśli jednak tworzysz projekt, który jest przeznaczony dla starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , nie możesz ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla profilu klienta dla [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] samego siebie. Aby rozwiązać ten problem, upewnij się, że aplikacja jest ukierunkowana na profil lub profile, które są zgodne z profilem, który jest przeznaczony dla projektów lub zestawów, do których odwołuje się aplikacja.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Projekt zostanie zmieniony na inną wersję .NET Framework  
 Jeśli zmienisz wersję docelową [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dla aplikacji, program Visual Studio zmieni niektóre odwołania, ale może być konieczne ręczne zaktualizowanie odwołań. Na przykład jeden z wymienionych wyżej błędów może wystąpić, jeśli zmienisz aplikację na docelową, [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] a ta aplikacja ma zasoby lub ustawienia, które opierają się na profilu klienta dla programu [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] .  
  
 Aby obejść ustawienia aplikacji, Otwórz **Eksplorator rozwiązań**, wybierz opcję **Pokaż wszystkie pliki**, a następnie edytuj plik app.config w edytorze XML programu Visual Studio. Zmień wersję w ustawieniach, aby dopasować ją do odpowiedniej wersji .NET Framework. Na przykład można zmienić ustawienie wersji z 4.0.0.0 na 2.0.0.0. Podobnie w przypadku aplikacji, która dodała zasoby, Otwórz **Eksplorator rozwiązań**, wybierz przycisk **Pokaż wszystkie pliki** , rozwiń **mój projekt** (Visual Basic) lub **Właściwości** (C#), a następnie edytuj plik resources. resx w edytorze XML programu Visual Studio. Zmień ustawienie wersji z 4.0.0.0 na 2.0.0.0.  
  
 Jeśli aplikacja zawiera zasoby, takie jak ikony lub mapy bitowe lub ustawienia, takie jak parametry połączenia danych, można również rozwiązać ten problem, usuwając wszystkie elementy na stronie **Ustawienia** **projektanta projektu** , a następnie ponownie dodając wymagane ustawienia.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Projekt zostanie zmieniony na inną wersję .NET Framework i odwołania nie są rozpoznawane  
 Jeśli przekierujesz projekt do innej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , odwołania w niektórych przypadkach mogą nie zostać prawidłowo rozwiązane. Jawne w pełni kwalifikowane odwołania do zestawów często powodują ten problem, ale można je rozwiązać, usuwając odwołania, które nie są rozpoznawane, a następnie dodając je z powrotem do projektu. Alternatywnie można edytować plik projektu, aby zastąpić odwołania. Najpierw należy usunąć odwołania do następującej postaci:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Następnie zastąp je prostą formą:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> Po zamknięciu i ponownym otwarciu projektu należy również ponownie skompilować go, aby upewnić się, że wszystkie odwołania zostały poprawnie rozwiązane.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: docelowa wersja .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework profilu klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Określanie konkretnej wersji .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Wielowersyjności kodu](../msbuild/msbuild-multitargeting-overview.md)
