---
title: -ResetAddin (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 241d97dd7b2b939ff49656e2cef2c93e4cb9b57b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656046"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usuwa poleceń i polecenia interfejs użytkownika skojarzony z określonym dodatku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argumenty  
 `AddIn`  
 Opcjonalna. Nazwa polecenia dodatku.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie nazwa polecenia dodatku jest równa  *\<AddInSolutionName >*. Połącz<em>.\< AddInSolutionName ></em>i pojawia się w Connect.cs jako `commandName` parametru `Exec` metody. Nazwę polecenia można również sprawdzić, zaczynając wpisywanie nazwy dodatku w oknie polecenia w programie Visual Studio, a następnie wypełniając pozostałe za pomocą technologii Intellisense.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie uruchamia programu Visual Studio i zapobiega `MyAddin` dodatek podczas uruchamiania systemu.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
