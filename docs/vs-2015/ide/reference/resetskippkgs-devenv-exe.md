---
title: -ResetSkipPkgs (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 207ceb92d84c2186aeec49c205d8d32f4d7aa969
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665575"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Czyści wszystkie opcje, aby pominąć ładowanie dodane do pakietów VSPackage przez użytkowników, którzy chcą uniknąć ładowania problemu pakietów VSPackage, a następnie uruchomi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Składnia

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Uwagi
 Obecność tagu SkipLoading wyłącza ładowanie pakietu VSPackage; Wyczyszczenie znacznika powoduje ponowne włączenie ładowania pakietu VSPackage.

## <a name="example"></a>Przykład
 Poniższy przykład czyści wszystkie Tagi SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Zobacz też
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
