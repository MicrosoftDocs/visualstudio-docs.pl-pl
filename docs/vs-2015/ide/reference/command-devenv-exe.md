---
title: -Polecenie (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9083d14c82eb2d283431e28d03bbbf96c14258cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660853"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wykonuje określone polecenie po uruchomieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```
devenv /command CommandName
```

## <a name="arguments"></a>Argumenty
 `CommandName` Wymagane. Pełna nazwa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] polecenia lub jego alias ujęty w znaki podwójnego cudzysłowu. Aby uzyskać więcej informacji na temat składni poleceń i aliasów, zobacz [Visual Studio Commands](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Uwagi
 Po zakończeniu uruchamiania środowisko IDE wykonuje nazwane polecenie. W przypadku użycia tego przełącznika IDE nie wyświetla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] strony początkowej przy uruchamianiu.

 Jeśli dodatek uwidacznia polecenie, można użyć tego przełącznika, aby uruchomić dodatek z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [jak: kontrolowanie dodatków za pomocą Menedżera dodatków](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Przykład
 Ten przykład uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i automatycznie uruchamia makro Otwórz Ulubione pliki.

```
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Zobacz też
 [Devenv — polecenie przełącza](../../ide/reference/devenv-command-line-switches.md) [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
