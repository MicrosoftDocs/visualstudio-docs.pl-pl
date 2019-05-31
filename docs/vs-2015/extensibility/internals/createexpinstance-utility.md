---
title: Narzędzie CreateExpInstance | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783709"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą narzędzie CreateExpInstance utworzyć, zresetować lub usunąć wystąpienie eksperymentalne programu Visual Studio. Wystąpienie eksperymentalne umożliwia debugowanie i testowanie rozszerzenia programu Visual Studio bez zmiany podstawowego produktu.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parametry  
 /Create  
 Tworzy wystąpienie eksperymentalne.  
  
 / Reset  
 Usuwa wystąpienie eksperymentalne programu, a następnie tworzy nową.  
  
 /Clean  
 Usuwa wystąpienie eksperymentalne.  
  
 /VSInstance  
 Nazwa katalogu, który zawiera wystąpienie programu Visual Studio w podstawowej, aby skopiować.  
  
 /RootSuffix  
 Sufiks, który można dołączyć do nazwy katalogu, w eksperymentalnym wystąpieniu.  
  
## <a name="remarks"></a>Uwagi  
 Podczas pracy w rozszerzeniu Visual Studio, można nacisnąć F5, aby otworzyć domyślne wystąpienie doświadczalne i zainstaluj rozszerzenie bieżącego. Jeśli żadne wystąpienie doświadczalne jest dostępny, program Visual Studio tworzy jeden, który zawiera ustawienia domyślne.  
  
 Domyślna lokalizacja wystąpienie doświadczalne zależy od numeru wersji programu Visual Studio. Na przykład dla programu Visual Studio 2015, lokalizacja jest %localappdata%\Microsoft\VisualStudio\14.0Exp\ wszystkie pliki w lokalizacji katalogu są traktowane jako część tego wystąpienia. Wszelkie dodatkowe wystąpienia doświadczalnego nie zostanie załadowany przez program Visual Studio, chyba, że nazwa katalogu jest zmieniana na lokalizację domyślną.  
  
 Program Visual Studio nie uzyskać dostępu do rejestru systemowego, po otwarciu wystąpienie eksperymentalne. Różni się to z wcześniejszych wersji programu Visual Studio, które są używane w wersji doświadczalnej gałęzi rejestru.  
  
 Narzędzie CreateExpInstance zastępuje narzędzie VsRegEx.  
  
 Poniższy przykład Resetuje domyślne doświadczalnym wystąpieniu programu Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)
