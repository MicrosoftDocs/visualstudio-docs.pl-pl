---
title: Lista modułów — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7d24b081c20b5874d6daa57832136023ac678c0f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199155"
---
# <a name="list-modules-command"></a>Lista modułów — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla listę modułów dla bieżącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Parametry  
 / Adres:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana adresów pamięci modułów. Wartość domyślna to `yes`.  
  
 / Name:`yes|no`  
 Opcjonalna. Określa, czy pokazać nazwy modułów. Wartość domyślna to `yes`.  
  
 / Order:`yes|no`  
 Opcjonalna. Określa, czy z kolejnością modułów. Wartość domyślna to `no`.  
  
 / Path:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana ścieżki modułów. Wartość domyślna to `yes`.  
  
 / Process:`yes|no`  
 Opcjonalny. Określa, czy ma być wyświetlana procesy modułów. Wartość domyślna to `no`.  
  
 /SymbolFile:`yes|no`  
 Opcjonalny. Określa, czy ma być wyświetlana pliki symboli modułów. Wartość domyślna to `no`.  
  
 / SymbolStatus:`yes|no`  
 Opcjonalny. Określa, czy mają być wyświetlane stany symboli modułów. Wartość domyślna to `yes`.  
  
 / Sygnatura czasowa:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana sygnatury czasowe modułów. Wartość domyślna to `no`.  
  
 / Version:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana wersje modułów. Wartość domyślna to `no`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zawiera listę nazw modułów, adresów i sygnatury czasowe dla bieżącego procesu.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Instrukcje: Korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)
