---
title: Narzędzia lokalizacyjne
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c6934c816574796d59f978c3d2f37f590cf578
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565126"
---
# <a name="develop-globalized-and-localized-apps"></a>Opracowywanie aplikacji globalnych i zlokalizowanych

Program Visual Studio ułatwia tworzenie użytkowników w różnych krajach, wykorzystując usługi wbudowane w [platformę .NET](/dotnet/standard/globalization-localization/).

Na przykład system projektu dla aplikacji Windows Forms może generować pliki zasobów dla rezerwowej kultury interfejsu użytkownika i każdej dodatkowej kultury interfejsu użytkownika. Podczas kompilowania projektu w programie Visual Studio pliki zasobów są kompilowane z formatu XML programu Visual Studio (resx) do pośredniego formatu binarnego (. resources), które są następnie osadzone w zestawach satelickich. Aby uzyskać więcej informacji, zobacz [pliki zasobów w programie Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) i [Tworzenie zestawów satelickich dla aplikacji klasycznych](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Języki dwukierunkowe

Za pomocą programu Visual Studio można tworzyć aplikacje, które prawidłowo wyświetlają tekst w językach pisanych od prawej do lewej, w tym arabski i hebrajski. W przypadku niektórych funkcji można po prostu ustawić właściwości. W innych przypadkach należy zaimplementować funkcje w kodzie.

> [!NOTE]
> Aby móc wprowadzać i wyświetlać języki dwukierunkowe, musisz pracować z wersją systemu Windows, która jest skonfigurowana przy użyciu odpowiedniego języka. Może to być angielska wersja systemu Windows z zainstalowanym odpowiednim pakietem językowym lub odpowiednio zlokalizowaną wersją systemu Windows.

### <a name="apps-that-support-bidirectional-languages"></a>Aplikacje obsługujące Języki dwukierunkowe

- Aplikacje dla systemu Windows

   Można tworzyć w pełni dwukierunkowe aplikacje, które obejmują obsługę tekstu dwukierunkowego, kolejność odczytywania od prawej do lewej i dublowanie (odwracanie układu okien, menu, okien dialogowych itd.). Z wyjątkiem dublowania te funkcje są dostępne domyślnie lub jako ustawienia właściwości. Dublowanie jest obsługiwane w sposób niezależny dla niektórych funkcji, takich jak okna komunikatów. Jednak w innych przypadkach należy zaimplementować dublowanie w kodzie. Aby uzyskać więcej informacji, zobacz [Obsługa dwukierunkowych aplikacji Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Aplikacje internetowe

   Usługi sieci Web obsługują wysyłanie i otrzymywanie tekstu UTF-8 i Unicode, dzięki czemu są odpowiednie dla aplikacji, które zawierają języki dwukierunkowe. Aplikacje klienckie sieci Web korzystają z przeglądarek dla ich interfejsów użytkownika, więc stopień dwukierunkowego wsparcia w aplikacji sieci Web zależy od tego, jak dobrze przeglądarka użytkownika obsługuje te funkcje dwukierunkowe. W programie Visual Studio można tworzyć aplikacje obsługujące tekst arabski lub hebrajski, kolejność odczytywania od prawej do lewej, kodowanie plików i ustawienia kultur lokalnych. Aby uzyskać więcej informacji, zobacz [dwukierunkowe wsparcie dla aplikacji sieci web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

> [!NOTE]
> Aplikacje konsolowe nie obejmują obsługi tekstu w językach dwukierunkowych. Jest to wynikiem działania systemu Windows z aplikacjami konsolowymi.

## <a name="see-also"></a>Zobacz także

- [Obsługa języków dwukierunkowych w programie Visual Studio](use-bidirectional-languages.md)
- [Globalizacja i lokalizowanie aplikacji platformy .NET](/dotnet/standard/globalization-localization/)
- [Zasoby w aplikacjach .NET](/dotnet/framework/resources/)
