---
title: ShowWebBrowser — — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663522"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla adres URL określony w oknie przeglądarki sieci Web w zintegrowanym środowisku programistycznym (IDE) lub zewnętrznym z IDE.

## <a name="syntax"></a>Składnia

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
 `URL` Wymagane. Adres URL (Uniform Resource Locator) witryny sieci Web.

## <a name="switches"></a>Przełączniki
 /New opcjonalne. Określa, że strona pojawia się w nowym wystąpieniu przeglądarki sieci Web.

 /EXT opcjonalne. Określa, że strona jest wyświetlana w domyślnej przeglądarce sieci Web poza IDE.

## <a name="remarks"></a>Uwagi
 Alias dla polecenia **ShowWebBrowser —** to **Nawigacja** lub **Nawigacja**.

## <a name="example"></a>Przykład
 Poniższy przykład wyświetla stronę główną MSDN Online w przeglądarce internetowej poza IDE. Jeśli wystąpienie przeglądarki sieci Web jest już otwarte, jest używane; w przeciwnym razie zostanie uruchomione nowe wystąpienie.

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
