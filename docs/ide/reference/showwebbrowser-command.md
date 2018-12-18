---
title: ShowWebBrowser — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87536df138de092948d845cf05d20af8e63ad68a
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672148"
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