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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747716"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie

Wyświetla adres URL określony w oknie przeglądarki sieci Web w zintegrowanym środowisku programistycznym (IDE) lub zewnętrznym z IDE.

## <a name="syntax"></a>Składnia

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
`URL`

Wymagany. Adres URL (Uniform Resource Locator) dla witryny sieci Web.

## <a name="switches"></a>Przełączniki
/new

Opcjonalny. Określa, że strona pojawia się w nowym wystąpieniu przeglądarki sieci Web.

/ext

Opcjonalny. Określa, że strona jest wyświetlana w domyślnej przeglądarce sieci Web poza IDE.

## <a name="remarks"></a>Uwagi
Alias dla polecenia **ShowWebBrowser —** to **Nawigacja** lub **Nawigacja**.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia Microsoft Docs stronie głównej w przeglądarce sieci Web poza IDE. Jeśli wystąpienie przeglądarki sieci Web jest już otwarte, jest używane; w przeciwnym razie zostanie uruchomione nowe wystąpienie.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)