---
title: ShowWebBrowser — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a46f37f93340226c669df5db59745af17c7b2464
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958891"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie

Wyświetla adres URL w oknie przeglądarki sieci web w ramach zintegrowanego środowiska programistycznego (IDE) lub zewnętrznego dla IDE.

## <a name="syntax"></a>Składnia

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
 `URL`

 Wymagana. Adres URL (Uniform Resource Locator) dla witryny sieci Web.

## <a name="switches"></a>Przełączniki
 / Nowy

 Opcjonalna. Określa, czy strona jest wyświetlana w nowym wystąpieniu przeglądarki sieci web.

 /ext

 Opcjonalna. Określa, czy strona jest wyświetlana w domyślnej przeglądarce sieci web poza IDE.

## <a name="remarks"></a>Uwagi
 Alias **showwebbrowser —** polecenie jest **Przejdź** lub **nav**.

## <a name="example"></a>Przykład
 Poniższy przykład wyświetla Microsoft Docs strony głównej w przeglądarce sieci web poza IDE. Jeśli wystąpienie przeglądarki sieci web jest już otwarty, jest używany; w przeciwnym razie jest uruchamiana nowe wystąpienie.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)