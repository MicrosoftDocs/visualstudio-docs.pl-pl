---
title: Polecenie wyjściowe okna polecenia dziennika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be51445940816f0feffcbc7ba0e542e94d0f0648
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791605"
---
# <a name="log-command-window-output-command"></a>Zapisuj dane wyjściowe okna Polecenie — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kopiuje wszystkie wejścia i wyjścia z **polecenia** okna w pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Opcjonalna. Nazwa pliku dziennika. Domyślnie plik jest tworzony w folderze profilu użytkownika. Jeśli nazwa pliku już istnieje, dziennik jest dołączany na końcu istniejącego pliku. Jeśli plik nie zostanie określony, ostatni określony plik jest używany. Jeśli nie poprzedni plik istnieje, utworzona jest domyślny plik dziennika o nazwie cmdline.log.  
  
> [!TIP]
>  Aby zmienić lokalizację, w której zostanie zapisany plik dziennika, należy wprowadzić pełną ścieżkę pliku ujęta w cudzysłów, jeżeli ścieżka zawiera spacje.  
  
## <a name="switches"></a>Przełączniki  
 /on  
 Opcjonalna. Rozpoczyna się w dzienniku **polecenia** okna w określonym pliku i dołącza plik o nowe informacje.  
  
 / off  
 Opcjonalna. Zatrzymuje się w dzienniku **polecenia** okna.  
  
 /overwrite  
 Opcjonalna. Jeżeli plik określony w `filename` argumentów pasuje do istniejącego pliku, plik jest zastępowany.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik nie zostanie określony, domyślnie jest tworzone cmdline.log pliku. Domyślnie alias dla tego polecenia jest dziennika.  
  
## <a name="examples"></a>Przykłady  
 W tym przykładzie tworzy nowy plik dziennika cmdlog i rozpoczyna się w dzienniku polecenia.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 W tym przykładzie zatrzymuje rejestrowanie poleceń.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 W tym przykładzie wznawia rejestrowanie poleceń w pliku dziennika stosowanych wcześniej.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
