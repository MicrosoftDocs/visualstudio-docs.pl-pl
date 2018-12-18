---
title: -Command (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2ee6f1166a543cc3dc85dfb62d19d1c5b194a16
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948169"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Wykonuje określone polecenie po uruchomieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>Argumenty
 `CommandName` Wymagane. Pełna nazwa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia lub jego alias, ujęte w podwójny cudzysłów. Aby uzyskać więcej informacji o syntaksie aliasów i poleceń, zobacz [polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Uwagi
 Po zakończeniu uruchamiania, IDE wykonuje polecenie nazwane. Jeśli używasz tego przełącznika, IDE nie wyświetla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] strony początkowej podczas uruchamiania.

 Jeśli dodatek udostępnia polecenia, można użyć tego przełącznika, aby uruchomić dodatek z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [instrukcje: kontrolki Add-Ins za pomocą Menedżera dodatków](https://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Przykład
 W tym przykładzie uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i automatycznie uruchamia makro otwierania ulubionych plików.

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)