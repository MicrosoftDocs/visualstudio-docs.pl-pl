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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565126"
---
# <a name="develop-globalized-and-localized-apps"></a>Tworzenie zglobalizowanych i zlokalizowanych aplikacji

Program Visual Studio ułatwia tworzenie dla międzynarodowej grupy odbiorców dzięki wykorzystaniu usług wbudowanych w [program .NET.](/dotnet/standard/globalization-localization/)

Na przykład system projektu dla aplikacji Windows Forms może generować pliki zasobów zarówno dla kultury rezerwowej interfejsu użytkownika, jak i każdej dodatkowej kultury interfejsu użytkownika. Podczas tworzenia projektu w programie Visual Studio pliki zasobów są kompilowane z formatu XML programu Visual Studio (.resx) do pośredniego formatu binarnego (.resources), które są następnie osadzane w zestawach satelickich. Aby uzyskać więcej informacji, zobacz [Pliki zasobów w programie Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) i Tworzenie [zestawów satelickich dla aplikacji klasycznych](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Języki dwukierunkowe

Za pomocą programu Visual Studio można tworzyć aplikacje, które poprawnie wyświetlają tekst w językach pisanych od prawej do lewej, w tym arabskim i hebrajskim. W przypadku niektórych funkcji można po prostu ustawić właściwości. W innych przypadkach należy zaimplementować funkcje w kodzie.

> [!NOTE]
> Aby można było wprowadzać i wyświetlać języki dwukierunkowe, należy pracować z wersją systemu Windows skonfigurowaną w odpowiednim języku. Może to być angielska wersja systemu Windows z zainstalowanym odpowiednim pakietem językowym lub odpowiednio zlokalizowana wersja systemu Windows.

### <a name="apps-that-support-bidirectional-languages"></a>Aplikacje obsługujące języki dwukierunkowe

- Aplikacja systemu Windows

   Można tworzyć w pełni dwukierunkowe aplikacje, które obejmują obsługę tekstu dwukierunkowego, kolejność czytania od prawej do lewej i dublowanie (odwrócenie układu okien, menu, okien dialogowych itd.). Z wyjątkiem dublowania, te funkcje są dostępne domyślnie lub jako ustawienia właściwości. Dublowanie jest obsługiwane z natury dla niektórych funkcji, takich jak pola komunikatów. Jednak w innych przypadkach należy zaimplementować dublowanie w kodzie. Aby uzyskać więcej informacji, zobacz [dwukierunkową obsługę aplikacji Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Aplikacje internetowe

   Usługi sieci Web obsługują wysyłanie i odbieranie tekstu UTF-8 i Unicode, dzięki czemu są odpowiednie dla aplikacji, które obejmują języki dwukierunkowe. Aplikacje klienckie sieci Web opierają się na przeglądarkach dla ich interfejsu użytkownika, więc stopień dwukierunkowej obsługi w aplikacji sieci web zależy od tego, jak dobrze przeglądarka użytkownika obsługuje te funkcje dwukierunkowe. W programie Visual Studio można tworzyć aplikacje z obsługą tekstu arabskiego lub hebrajskiego, kolejności odczytu od prawej do lewej, kodowaniem plików i ustawieniami kultury lokalnej. Aby uzyskać więcej informacji, zobacz [Dwukierunkowa obsługa ASP.NET aplikacji sieci Web](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

> [!NOTE]
> Aplikacje konsoli nie zawierają obsługi tekstu dla języków dwukierunkowych. Jest to konsekwencją tego, jak system Windows współpracuje z aplikacjami konsoli.

## <a name="see-also"></a>Zobacz też

- [Obsługa języków dwukierunkowych w programie Visual Studio](use-bidirectional-languages.md)
- [Zglobalizuj i lokalizuj aplikacje .NET](/dotnet/standard/globalization-localization/)
- [Zasoby w aplikacjach .NET](/dotnet/framework/resources/)
