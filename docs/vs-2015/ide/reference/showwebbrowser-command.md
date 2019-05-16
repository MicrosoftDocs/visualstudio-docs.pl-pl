---
title: Showwebbrowser — polecenie | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3cd5d04efab6f6cb5641c7e0c4c2a8547e1ef00
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689414"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla adres URL w oknie przeglądarki sieci Web w ramach zintegrowanego środowiska programistycznego (IDE) lub zewnętrznego dla IDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Argumenty  
 `URL`  
 Wymagana. Adres URL (Uniform Resource Locator) dla witryny sieci Web.  
  
## <a name="switches"></a>Przełączniki  
 / Nowy  
 Opcjonalna. Określa, czy strona jest wyświetlana w nowym wystąpieniu przeglądarki sieci Web.  
  
 /ext  
 Opcjonalna. Określa, czy strona jest wyświetlana w domyślnej przeglądarce sieci Web poza IDE.  
  
## <a name="remarks"></a>Uwagi  
 Alias **showwebbrowser —** polecenie jest **Przejdź** lub **nav**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wyświetla MSDN Online strony głównej w przeglądarce sieci Web poza IDE. Jeśli wystąpienie przeglądarki sieci Web jest już otwarty, jest używany; w przeciwnym razie jest uruchamiana nowe wystąpienie.  
  
```  
>View.ShowWebBrowser https://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
