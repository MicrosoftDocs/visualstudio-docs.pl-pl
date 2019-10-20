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
ms.openlocfilehash: 292910cb75ba9f69a7d8fc231ca6574ccf8bbfbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645247"
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

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)