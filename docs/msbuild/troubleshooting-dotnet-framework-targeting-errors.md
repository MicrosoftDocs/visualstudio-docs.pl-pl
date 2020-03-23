---
title: Rozwiązywanie problemów z błędami kierowania programu .NET Framework | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1c496fd457e80220bb2ea4a2f032cef9508d9dcb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631604"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Rozwiązywanie problemów z błędami kierowania programu .NET Framework

W tym temacie opisano błędy MSBuild, które mogą wystąpić z powodu problemów z odwołaniem i jak można rozwiązać te błędy.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odwołujesz się do projektu lub zestawu przeznaczonego dla innej wersji programu .NET Framework

 Można tworzyć aplikacje, które odwołują się do projektów lub zestawów, które są przeznaczone dla różnych wersji programu .NET Framework. Na przykład można utworzyć aplikację, która jest przeznaczona dla profilu klienta dla programu .NET Framework 4, ale odwołuje się do zestawu, który jest przeznaczony dla programu .NET Framework 2.0. Jednak jeśli utworzysz projekt, który jest przeznaczony dla wcześniejszej wersji programu .NET Framework, nie można ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla profilu klienta dla programu .NET Framework 4 lub .NET Framework 4. Aby rozwiązać ten błąd, upewnij się, że aplikacja jest przeznaczona dla profilu lub profili, które są zgodne z profilem, który jest przeznaczony dla projektów lub zestawów, do których odwołuje się aplikacja.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Projekt został ponownie skierowany do innej wersji programu .NET Framework

 Jeśli zmienisz docelową wersję programu .NET Framework dla aplikacji, program Visual Studio zmieni niektóre odwołania, ale może być konieczne ręczne zaktualizowanie niektórych odwołań. Na przykład jeden z wcześniej wymienionych błędów może wystąpić, jeśli zmienisz aplikację na docelową usługę .NET Framework 3.5 z dodatkiem Service Pack 1, a ta aplikacja ma zasoby lub ustawienia, które opierają się na profilu klienta dla programu .NET Framework 4.

 Aby obejść ustawienia aplikacji, otwórz **Eksploratora rozwiązań**, wybierz pozycję **Pokaż wszystkie pliki**, a następnie edytuj plik *app.config* w edytorze XML programu Visual Studio. Zmień wersję w ustawieniach, aby dopasować odpowiednią wersję programu .NET Framework. Na przykład można zmienić ustawienie wersji z 4.0.0.0 na 2.0.0.0. Podobnie dla aplikacji, która dodała zasoby, otwórz **Eksploratora rozwiązań**, wybierz przycisk **Pokaż wszystkie pliki,** rozwiń **mój projekt** (Visual Basic) lub **Właściwości** (C#), a następnie edytuj plik *Resources.resx* w edytorze XML programu Visual Studio. Zmień ustawienie wersji z 4.0.0.0 na 2.0.0.0.

 Jeśli aplikacja ma zasoby, takie jak ikony lub mapy bitowe lub ustawienia, takie jak parametry połączenia danych, można również rozwiązać ten błąd, usuwając wszystkie elementy na stronie **Ustawienia** **projektanta projektu,** a następnie ponownie dodając wymagane ustawienia.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Ponownie wycelowałeś projekt w inną wersję programu .NET Framework, a odwołania nie są rozpoznawane

 Jeśli ponownie przekierować projekt do innej wersji programu .NET Framework, odwołania mogą nie rozwiązać poprawnie w niektórych przypadkach. Jawne w pełni kwalifikowane odwołania do zestawów często powodują ten problem, ale można go rozwiązać, usuwając odwołania, które nie zostały rozpoznane, a następnie dodając je z powrotem do projektu. Alternatywnie można edytować plik projektu, aby zastąpić odwołania. Najpierw należy usunąć odwołania do następującego formularza:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Następnie można je zastąpić prostą formą:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Po zamknięciu i ponownym otwarciu projektu należy również odbudować go, aby upewnić się, że wszystkie odwołania są poprawnie rozpoznawane.

## <a name="see-also"></a>Zobacz też

- [Jak: Kierowanie na wersję programu .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Profil klienta programu .NET Framework](/dotnet/framework/deployment/client-profile)
- [Omówienie kierowania na ramy](../ide/visual-studio-multi-targeting-overview.md)
- [Wielotargowe](../msbuild/msbuild-multitargeting-overview.md)
