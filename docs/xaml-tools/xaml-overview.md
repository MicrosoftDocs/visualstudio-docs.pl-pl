---
title: Przegląd XAML
ms.date: 07/31/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9b04012e2f0b046b3fd31058c9838740e833281
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450892"
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

Program Visual Studio i Blend for Visual Studio udostępniają projektant XAML, które pomagają tworzyć interfejsy użytkownika dla aplikacji WPF, platformy UWP i Xamarin. Forms. Kontrolki można przeciągać z okna przybornika lub zasobów i ustawiać właściwości w okno Właściwości. Podczas wykonywania tych akcji program Visual Studio i Blend for Visual Studio tworzą odpowiedni kod XAML. Jeśli wolisz edytować kod XAML bezpośrednio, możesz to zrobić.

Artykuły w tym zestawie dokumentacji omawiają projektant XAML w programie Visual Studio i Blend for Visual Studio.

## <a name="see-also"></a>Zobacz także

- [XAML w aplikacjach WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML w aplikacjach Xamarin. Forms](/xamarin/xamarin-forms/xaml/)