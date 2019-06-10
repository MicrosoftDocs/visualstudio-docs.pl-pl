---
title: Narzędzia do lokalizacji
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 934427c2bfba769968b7aeb364625b71af47eca7
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820870"
---
# <a name="develop-globalized-and-localized-apps"></a>Tworzenie aplikacji uniwersalnych i zlokalizowanych

Program Visual Studio sprawia, że tworzenie aplikacji dla publiczności międzynarodowej łatwe dzięki wykorzystaniu usług, wbudowaną [.NET](/dotnet/standard/globalization-localization/).

Na przykład system projektu dla aplikacji Windows Forms można wygenerować plików zasobów dla rezerwowego kultura interfejsu użytkownika i każdego dodatkowego kultura interfejsu użytkownika. Podczas tworzenia projektu w programie Visual Studio, pliki zasobów są kompilowane z formatu programu Visual Studio XML (resx) na pośrednie format binarny (.resources), które następnie są osadzone w zestawach satelickich. Aby uzyskać więcej informacji, zobacz [pliki zasobów w programie Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) i [tworzenie zestawów satelickich dla aplikacji klasycznych](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Języki dwukierunkowe

Visual Studio umożliwia tworzenie aplikacji, które poprawnie wyświetlania tekstu w językach zapisywane prawej do lewej, łącznie z arabski i hebrajski. W przypadku niektórych funkcji można po prostu ustaw właściwości. W innych przypadkach należy zaimplementować funkcje w kodzie.

> [!NOTE]
> Aby można było wprowadzanie i wyświetlanie języki dwukierunkowe, musisz pracować z wersją systemu Windows, który jest skonfigurowany przy użyciu odpowiedniego języka. Może to być angielska wersja systemu Windows przy użyciu odpowiedniego pakietu języka zainstalowane lub prawidłowo zlokalizowaną wersję Windows.

### <a name="apps-that-support-bidirectional-languages"></a>Aplikacje, które obsługują języki dwukierunkowe

- Aplikacje Windows

   Możesz utworzyć w pełni aplikacjach, które obejmują obsługę tekstu dwukierunkowego, od prawej do lewej kolejność czytania i dublowanie (cofania układu systemu windows, menu, okna dialogowe i tak dalej). Z wyjątkiem funkcji dublowania, te funkcje są dostępne, domyślnie lub zgodnie z ustawieniami właściwości. Dublowanie obsługę natury niektóre funkcje, takie jak okna komunikatów. Jednak w innych przypadkach należy zaimplementować dublowania w kodzie. Aby uzyskać więcej informacji, zobacz [Dwukierunkowa obsługa aplikacji Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Aplikacje internetowe

   Obsługa usług sieci Web, wysyłanie i odbieranie UTF-8 i tekst w formacie Unicode, czemu są odpowiednie dla aplikacji, które obejmują języki dwukierunkowe. Zależą od przeglądarki dla interfejsu użytkownika aplikacji klienta sieci Web, więc stopień dwukierunkowe obsługuje w aplikacji sieci web jest zależny od stopnia przeglądarki użytkownika obsługuje te funkcje dwukierunkowy. W programie Visual Studio możesz tworzyć aplikacje z obsługą tekst arabski lub hebrajski, kolejność czytania od prawej do lewej, kodowanie pliku i ustawienia lokalnych kultury. Aby uzyskać więcej informacji, zobacz [Dwukierunkowa obsługa aplikacji sieci web platformy ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

> [!NOTE]
> Aplikacje konsoli nie uwzględniają tekstu Obsługa języków dwukierunkowych. Jest to wynikiem sposobu działania Windows za pomocą aplikacji konsoli.

## <a name="see-also"></a>Zobacz także

- [Obsługa języków dwukierunkowych w programie Visual Studio](use-bidirectional-languages.md)
- [Sprzedawać i lokalizować aplikacje platformy .NET](/dotnet/standard/globalization-localization/)
- [Zasoby w aplikacjach .NET](/dotnet/framework/resources/)