---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657919"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Powiadamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o scaleniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pakietów w systemie i sprawdź pamięć podręczną MEF pod kątem wszelkich zmian.

## <a name="syntax"></a>Składnia

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Uwagi
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchamia to polecenie automatycznie po zainstalowaniu pakietu VSIX. Należy uruchomić `devenv.exe /updateconfiguration` po zainstalowaniu poprawek plików, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zaktualizować pamięć podręczną MEF. Dzięki temu można sprawdzić, czy poprawka jest odpowiednia.

## <a name="example"></a>Przykład
 Poniższy wiersz polecenia powoduje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] scalenie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pakietów w systemie i sprawdzenie, czy w pamięci podręcznej MEF wprowadzono zmiany.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md)
