---
title: Przegląd XAML
description: Uzyskaj podstawowe informacje na temat języka XAML i edytora kodu XAML oraz narzędzi projektant XAML w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 6f315573b24989e6ad3a3d451de372430b72f70f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931201"
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

## <a name="xaml-code-editor"></a>Edytor kodu XAML

[Edytor kodu XAML](xaml-code-editor.md) w środowisku IDE programu Visual Studio zawiera wszystkie narzędzia potrzebne do tworzenia aplikacji WPF i platformy UWP dla platformy systemu Windows oraz dla programu Xamarin. Forms. Mimo że IDE (zintegrowane środowisko programistyczne) w programie Visual Studio ma wiele funkcji, których można użyć do tworzenia aplikacji dla innych platform, także zawiera pewne funkcje, które są również unikatowe dla języka XAML.

## <a name="xaml-designer"></a>XAML Designer

Program Visual Studio i Blend for Visual Studio udostępniają [Projektant XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) , które pomagają tworzyć interfejsy użytkownika dla aplikacji WPF, platformy UWP i Xamarin. Forms. Kontrolki można przeciągać z okna przybornika lub zasobów i ustawiać właściwości w okno Właściwości. Gdy to zrobisz, program Visual Studio i Blend for Visual Studio utworzy odpowiedni kod XAML. Jeśli wolisz edytować kod XAML bezpośrednio, możesz to zrobić.

## <a name="whats-new"></a>Co nowego

Aby uzyskać najnowsze informacje, zapoznaj się z następującymi zasobami:

- **[Ulepszenia narzędzi XAML w programie Visual Studio 2019 w wersji 16,7 Preview 1 wpis na](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)** blogu
- Wpis w blogu dotyczący **[nowości w narzędziach deweloperskich XAML w programie Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- **[Nowe funkcje XAML w klipie wideo programu Visual Studio](https://youtu.be/yI9OyA4ZM2E)** w serwisie YouTube

## <a name="see-also"></a>Zobacz też

- [XAML w aplikacjach WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML w aplikacjach Xamarin. Forms](/xamarin/xamarin-forms/xaml/)
