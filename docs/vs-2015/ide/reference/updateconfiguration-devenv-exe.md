---
title: -Updateconfiguration (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657919"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv. exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Powiadamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w celu scalenia pakietów [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w systemie i sprawdź, czy w pamięci podręcznej MEF wprowadzono zmiany.

## <a name="syntax"></a>Składnia

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Uwagi
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchamia to polecenie automatycznie po zainstalowaniu pakietu VSIX. Należy uruchomić `devenv.exe /updateconfiguration` po zainstalowaniu poprawek plików, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zaktualizował pamięć podręczną MEF. Dzięki temu można sprawdzić, czy poprawka jest odpowiednia.

## <a name="example"></a>Przykład
 Poniższy wiersz polecenia powoduje, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] scalanie pakietów [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w systemie i sprawdzanie, czy w pamięci podręcznej MEF wprowadzono zmiany.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md)
