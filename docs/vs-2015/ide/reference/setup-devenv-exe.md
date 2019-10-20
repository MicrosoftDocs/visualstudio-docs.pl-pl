---
title: -Setup (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663535"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wymusza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] scalania metadanych zasobów, które opisują menu, paski narzędzi i grupy poleceń, ze wszystkich dostępnych pakietów VSPackage.

## <a name="syntax"></a>Składnia

```
devenv /setup
```

## <a name="remarks"></a>Uwagi
 Ten przełącznik nie przyjmuje żadnych argumentów. Polecenie `devenv /setup` jest zazwyczaj podawane jako ostatni krok procesu instalacji. Użycie przełącznika `/setup` nie powoduje uruchomienia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Aby używać przełączników [/Setup (devenv. exe)](../../ide/reference/setup-devenv-exe.md) i [/InstallVSTemplates (devenv. exe)](../../ide/reference/installvstemplates-devenv-exe.md) , należy uruchomić `devenv` jako administrator.

## <a name="example"></a>Przykład
 Ten przykład pokazuje ostatni krok instalacji wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], która zawiera pakietów VSPackage.

```
devenv /setup
```

## <a name="see-also"></a>Zobacz też
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
