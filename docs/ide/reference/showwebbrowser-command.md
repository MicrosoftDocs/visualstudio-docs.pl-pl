---
title: ShowWebBrowser — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8c97659cc6036433c5bcf2547a9f88aee56f451
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747716"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie

Wyświetla adres URL określony w oknie przeglądarki sieci Web w zintegrowanym środowisku programistycznym (IDE) lub zewnętrznym ide.

## <a name="syntax"></a>Składnia

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
`URL`

Wymagany. Adres URL (Uniform Resource Locator) dla witryny sieci Web.

## <a name="switches"></a>Przełączniki
/nowy

Element opcjonalny. Określa, że strona jest wyświetlana w nowym wystąpieniu przeglądarki sieci Web.

/ext

Element opcjonalny. Określa, że strona jest wyświetlana w domyślnej przeglądarce internetowej poza IDE.

## <a name="remarks"></a>Uwagi
Alias polecenia **ShowWebBrowser** to **nawigacja** lub **nawigacja**.

## <a name="example"></a>Przykład
W poniższym przykładzie jest wyświetlana strona główna Dokumentów Firmy Microsoft w przeglądarce sieci Web poza ideą. Jeśli wystąpienie przeglądarki internetowej jest już otwarte, jest używane; w przeciwnym razie zostanie uruchomione nowe wystąpienie.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)