---
title: Lista źródeł — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae2ed3e8a9c07d59f5b1c2fe2350956a54dfaa66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761510"
---
# <a name="list-source-command"></a>Lista źródeł — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Wyświetla określone linie kodu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Przełączniki  
 / Liczba:`number`  
 Opcjonalna. Określa liczbę wierszy do wyświetlenia.  
  
 / Bieżąca  
 Opcjonalna. Pokazuje bieżący wiersz.  
  
 /File:`filename`  
 Opcjonalna. Ścieżka pliku do wyświetlenia. Jeśli nazwa pliku nie zostanie określony, polecenie wyświetla kod źródłowy dla wiersza bieżącej instrukcji.  
  
 / Linii:`number`  
 Opcjonalna. Pokazuje określonego numeru wiersza.  
  
 / ShowLineNumbers:`yes|no`  
 Opcjonalna. Określa, czy wyświetlanie numerów wierszy.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono kod źródłowy z wiersz 4 pliku Form1.vb, za pomocą widoczne numery wierszy.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno Polecenie](../../ide/reference/command-window.md)
