---
title: -Edit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c81f59f2dadf535af4e9a76949a29fd1355c33f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657741"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otwiera określony plik w istniejącym wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="syntax"></a>Składnia

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Argumenty
 `file1` Obowiązkowe. Plik do otwarcia w istniejącym wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Jeśli wystąpienie nie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] istnieje, nowe wystąpienie jest tworzone z uproszczonym układem okna i `file1` zostanie otwarte w nowym wystąpieniu.

 `file2` Obowiązkowe. Co najmniej jeden dodatkowy plik do otwarcia w istniejącym wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="remarks"></a>Uwagi
 Jeśli plik nie zostanie określony i istnieje wystąpienie istniejącego wystąpienia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , istniejące wystąpienie elementu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] otrzymuje fokus. Jeśli plik nie zostanie określony i nie ma istniejącego wystąpienia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , nowe wystąpienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest tworzone z uproszczonym układem okna.

 Jeśli istniejące wystąpienie programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest w stanie modalnym, na przykład jeśli okno [dialogowe Opcje](../../ide/reference/options-dialog-box-visual-studio.md) jest otwarte, plik zostanie otwarty w istniejącym wystąpieniu podczas [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zamykania stanu modalnego.

## <a name="example"></a>Przykład
 Ten przykład otwiera plik `MyFile.cs` w istniejącym wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lub otwiera plik w nowym wystąpieniu, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Jeśli jeszcze nie istnieje.

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Zobacz też
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
