---
title: Narzędzie CreateExpInstance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d778f0f31a7651412915a898bff9e4bdfe6c55f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196982"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj narzędzia CreateExpInstance, aby utworzyć, zresetować lub usunąć eksperymentalne wystąpienie programu Visual Studio. Możesz użyć eksperymentalnego wystąpienia do debugowania i testowania rozszerzeń programu Visual Studio bez zmiany bazowego produktu.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parametry  
 /Create  
 Tworzy wystąpienie eksperymentalne.  
  
 /Reset  
 Usuwa wystąpienie eksperymentalne, a następnie tworzy nowe.  
  
 /Clean  
 Usuwa wystąpienie eksperymentalne.  
  
 /VSInstance  
 Nazwa katalogu zawierającego podstawowe wystąpienie programu Visual Studio do skopiowania.  
  
 /RootSuffix  
 Sufiks do dołączenia do nazwy eksperymentalnego katalogu wystąpień.  
  
## <a name="remarks"></a>Uwagi  
 Podczas pracy nad rozszerzeniem programu Visual Studio można nacisnąć klawisz F5, aby otworzyć domyślne wystąpienie eksperymentalne i zainstalować bieżące rozszerzenie. Jeśli żadne wystąpienie eksperymentalne nie jest dostępne, program Visual Studio tworzy taki, który ma ustawienia domyślne.  
  
 Domyślna lokalizacja wystąpienia doświadczalnego zależy od numeru wersji programu Visual Studio. Na przykład w przypadku programu Visual Studio 2015 lokalizacja jest%localappdata%\Microsoft\VisualStudio\14.0Exp\ wszystkie pliki w lokalizacji katalogu są uważane za część tego wystąpienia. Wszystkie dodatkowe eksperymentalne wystąpienia nie zostaną załadowane przez program Visual Studio, chyba że nazwa katalogu zostanie zmieniona na lokalizację domyślną.  
  
 Program Visual Studio nie uzyskuje dostępu do rejestru systemowego, gdy otwiera wystąpienie eksperymentalne. Różni się to od wcześniejszych wersji programu Visual Studio, które używały eksperymentalnej wersji gałęzi rejestru.  
  
 Narzędzie CreateExpInstance zastępuje narzędzie VsRegEx.  
  
 Poniższy przykład resetuje domyślne wystąpienie eksperymentalne programu Visual Studio.  
  
 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix = EXP**  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)
