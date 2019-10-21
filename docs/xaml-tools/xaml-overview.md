---
title: Przegląd XAML
ms.date: 07/31/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: af6ef98c5bffc4563cfa8fc8e0b29a910aeb85e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601870"
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