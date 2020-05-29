---
title: Przegląd XAML
ms.date: 05/20/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 97f3bc7777023903d5fc38ad1bda7cde45b683b6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183486"
---
# <a name="overview-of-xaml"></a>Przegląd języka XAML

Extensible Application Markup Language (XAML) to deklaratywny język oparty na języku XML. Język XAML jest szeroko używany w następujących typach aplikacji do kompilowania interfejsów użytkownika:

- [Aplikacje Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Aplikacje platforma uniwersalna systemu Windows (platformy UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Aplikacje platformy Xamarin. Forms](/xamarin/xamarin-forms/xaml/)

Poniższy kod XAML definiuje prostą kontrolkę Button.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

KOD XAML jest również używany do definiowania przepływów pracy w [aplikacjach Windows Workflow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-designer"></a>XAML Designer

Program Visual Studio i Blend for Visual Studio udostępniają projektant XAML, które pomagają tworzyć interfejsy użytkownika dla aplikacji WPF, platformy UWP i Xamarin. Forms. Kontrolki można przeciągać z okna przybornika lub zasobów i ustawiać właściwości w okno Właściwości. Gdy to zrobisz, program Visual Studio i Blend for Visual Studio utworzy odpowiedni kod XAML. Jeśli wolisz edytować kod XAML bezpośrednio, możesz to zrobić.

Artykuły w tym zestawie dokumentacji omawiają projektant XAML w programie Visual Studio i Blend for Visual Studio.

## <a name="whats-new"></a>Co nowego

Aby uzyskać najnowsze informacje, zapoznaj się z artykułem [co nowego w narzędziach programistycznych XAML w blogu programu Visual studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/) , [udoskonalenia narzędzi XAML w programie Visual Studio 2019 w wersji 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/) i [nowe funkcje XAML w programie Visual Studio](https://youtu.be/yI9OyA4ZM2E) wideo w witrynie YouTube.

## <a name="see-also"></a>Zobacz także

- [XAML w aplikacjach WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML w aplikacjach Xamarin. Forms](/xamarin/xamarin-forms/xaml/)
