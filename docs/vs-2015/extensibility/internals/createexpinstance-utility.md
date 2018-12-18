---
title: Narzędzie CreateExpInstance | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a6761e844cee41c1a6f0df79f0d6529f4a8215
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768261"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą narzędzie CreateExpInstance utworzyć, zresetować lub usunąć wystąpienie eksperymentalne programu Visual Studio. Wystąpienie eksperymentalne umożliwia debugowanie i testowanie rozszerzenia programu Visual Studio bez zmiany podstawowego produktu.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parametry  
 / Tworzenia  
 Tworzy wystąpienie eksperymentalne.  
  
 / Reset  
 Usuwa wystąpienie eksperymentalne programu, a następnie tworzy nową.  
  
 /Clean  
 Usuwa wystąpienie eksperymentalne.  
  
 / VSInstance  
 Nazwa katalogu, który zawiera wystąpienie programu Visual Studio w podstawowej, aby skopiować.  
  
 / RootSuffix  
 Sufiks, który można dołączyć do nazwy katalogu, w eksperymentalnym wystąpieniu.  
  
## <a name="remarks"></a>Uwagi  
 Podczas pracy w rozszerzeniu Visual Studio, można nacisnąć F5, aby otworzyć domyślne wystąpienie doświadczalne i zainstaluj rozszerzenie bieżącego. Jeśli żadne wystąpienie doświadczalne jest dostępny, program Visual Studio tworzy jeden, który zawiera ustawienia domyślne.  
  
 Domyślna lokalizacja wystąpienie doświadczalne zależy od numeru wersji programu Visual Studio. Na przykład dla programu Visual Studio 2015, lokalizacja jest %localappdata%\Microsoft\VisualStudio\14.0Exp\ wszystkie pliki w lokalizacji katalogu są traktowane jako część tego wystąpienia. Wszelkie dodatkowe wystąpienia doświadczalnego nie zostanie załadowany przez program Visual Studio, chyba, że nazwa katalogu jest zmieniana na lokalizację domyślną.  
  
 Program Visual Studio nie uzyskać dostępu do rejestru systemowego, po otwarciu wystąpienie eksperymentalne. Różni się to z wcześniejszych wersji programu Visual Studio, które są używane w wersji doświadczalnej gałęzi rejestru.  
  
 Narzędzie CreateExpInstance zastępuje narzędzie VsRegEx.  
  
 Poniższy przykład Resetuje domyślne doświadczalnym wystąpieniu programu Visual Studio.  
  
 **/VSInstance CreateExpInstance.exe/reset = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)

