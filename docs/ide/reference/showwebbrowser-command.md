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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8266a7c70544d8a320658fcd8b9f5ad249162fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769577"
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
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)