---
title: -ResetAddin (devenv. exe) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665602"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usuwa polecenia i interfejs użytkownika poleceń skojarzonych z określonym dodatkiem.

## <a name="syntax"></a>Składnia

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>Argumenty
 `AddIn` opcjonalny. Nazwa polecenia dodatku.

## <a name="remarks"></a>Uwagi
 Domyślnie nazwa polecenia dodatku jest równa *\<AddInSolutionName >* . Połącz<em>. \<AddInSolutionName ></em>i pojawia się w Connect.cs jako parametr `commandName` metody `Exec`. Możesz również zweryfikować nazwę polecenia, rozpoczynając od wpisania nazwy dodatku do okna poleceń w programie Visual Studio i używając funkcji IntelliSense do wypełnienia reszty.

## <a name="example"></a>Przykład
 Poniższy przykład uruchamia program Visual Studio i uniemożliwia uruchamianie dodatku `MyAddin` podczas uruchamiania.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md)
