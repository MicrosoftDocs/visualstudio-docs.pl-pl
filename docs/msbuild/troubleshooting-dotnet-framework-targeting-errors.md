---
title: Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3ebe0d73aa2cd4a030e99d4501c5d3d726888f64
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620294"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Rozwiązywanie problemów z błędami obiektów docelowych w .NET Framework
W tym temacie opisano błędy programu MSBuild, które mogą wystąpić z powodu odwołania problemy i jak można naprawić te błędy.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Ma odwołanie do projektu lub zestawu, który jest przeznaczony dla innej wersji programu .NET Framework
 Możesz tworzyć aplikacje odwołujące się do projektów lub zestawów, przeznaczonych dla różnych wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Na przykład utworzysz aplikację, który jest przeznaczony dla profilu klienta dla [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , ale odwołuje się do zestawu, który jest przeznaczony dla .NET Framework 2.0. Jednak jeśli tworzysz projekt, który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], nie można ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla profilu klienta dla [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] lub [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] sam. Aby naprawić błąd, upewnij się, że aplikacja jest przeznaczony dla profil lub profile, które są zgodne z profilem, który jest określony przez projektów lub zestawów, do których odwołuje się do aplikacji.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Jest ponownie skierowany projektu do innej wersji programu .NET Framework
 Jeśli zmienisz wersję docelową [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dla aplikacji, Visual Studio zmieniają niektóre odwołania, ale musisz ręcznie zaktualizować niektóre odwołania. Na przykład jeden z wymienionych wcześniej błędów może wystąpić, jeśli zmienisz aplikację docelową [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] i że aplikacja ma zasoby lub ustawień, które opierają się na profil klienta [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].

 Aby obejść ustawienia aplikacji, otwórz **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki**, a następnie Edytuj *app.config* plik w edytorze XML programu Visual Studio. Zmień wersję w ustawieniach, aby dopasować odpowiednią wersję programu .NET Framework. Na przykład można zmienić ustawienie wersji z 4.0.0.0, aby 2.0.0.0 lub nowszej. Podobnie, dla aplikacji, która została dodana zasobów, należy otworzyć **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** , rozwiń pozycję **mój projekt** (Visual Basic) lub **Właściwości** (C#), a następnie Edytuj *Resources.resx* plik w edytorze XML programu Visual Studio. Zmień ustawienie wersji z 4.0.0.0 na 2.0.0.0 lub nowszej.

 Jeśli aplikacja ma zasoby, takie jak ikony lub mapy bitowe lub ustawienia, takie jak parametry połączenia danych, można również rozwiązać błąd, usuwając wszystkie elementy na **ustawienia** stronie **projektanta projektu**, a następnie ponowne dodanie wymaganych ustawień.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Projekt do innej wersji programu .NET Framework jest ponownie skierowany i odwołania nie został rozwiązany
 Jeśli przekierowanie projektu do innej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], odwołaniami mogą nie być rozpoznawane prawidłowo w niektórych przypadkach. Jawne w pełni kwalifikowanego odwołania do zestawów często przyczyną tego problemu, ale można go naprawić przez usunięcie odwołania, które nie umożliwiają rozwiązania, a następnie dodanie ich do projektu. Alternatywnie można edytować plik projektu w celu zastąpienia odwołań. Najpierw należy usunąć odwołania następującą postać:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Następnie należy zastąpić je prostego formularza:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
>  Po zamknięciu i ponownym otwarciu projektu powinien również można odbudować ją, aby zapewnić poprawnie rozpoznać wszystkie odwołania.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [Profil klienta .NET framework](/dotnet/framework/deployment/client-profile)
- [Przeznaczone dla określonej wersji środowiska .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Wielowersyjność kodu](../msbuild/msbuild-multitargeting-overview.md)