---
title: Dostawca symboli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178889"
---
# <a name="symbol-provider"></a>Dostawca symboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Implementacja ewaluatora wyrażeń musi uzyskać dostęp do symbolicznych informacji debugowania generowanych przez kompilator języka w celu obliczenia zmiennych i wyrażeń. Robi to poprzez zużywanie interfejsów dostawcy symboli (SP), nazywanych również obsługą symboli.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostarcza program SPs dla kodu zarządzanego oraz kod natywny przy użyciu formatu pliku symboli bazy danych (PDB). Jeśli program nie ma silnej potrzeby używania symboli przechowywanych w formacie niestandardowym, zaleca się korzystanie z programu SPs dostarczonego przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Aparaty debugowania oczekują na rozmowę z programem SPS przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym, SP, który będzie pracował z aparatami debugowania programu Visual Studio, musi obsługiwać środowisko CLR. Pełną listę interfejsów debugowania CLR można znaleźć w debugref.doc, która jest częścią [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 Jeśli program SP będzie działał tylko z niestandardowym aparatem debugowania, można zaimplementować program SP w zależności od potrzeb aparatu debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)
