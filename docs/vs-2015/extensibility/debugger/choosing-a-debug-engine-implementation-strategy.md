---
title: Wybieranie strategii implementacji aparatu debugowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117697"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Wybieranie strategii implementacji aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Architektura środowiska wykonawczego umożliwia określenie strategii implementacji aparatu (DE) debugowania. Aparat debugowania może zostać utworzony wewnątrz procesu program do debugowania, w trakcie Menedżer debugowania sesji programu Visual Studio (SDM) lub poza procesem do obu z nich. Poniższe wskazówki pomoże wybrać jeden z tych trzech strategii.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Choć jest możliwe do DE to spoza procesu do SDM i program do debugowania, zwykle nie ma powodu aby to zrobić. Wywołania przez granice procesu są stosunkowo wolno.  
  
 Debugowanie aparaty są już udostępniane dla środowiska wykonawczego natywny Win32 i środowiska uruchomieniowego języka wspólnego. Jeśli musisz zastąpić DE dla jednej z tych środowisk, należy utworzyć z SDM DE w procesie.  
  
 W przeciwnym razie możesz wybrać opcję tworzenia DE wewnątrz procesu SDM lub proces programu do debugowania. Należy wziąć pod uwagę czy ewaluatora wyrażenia z DE wymaga częstego dostępu do magazynu symboli programu i czy można załadować do pamięci w celu szybkiego dostępu do magazynu symboli. Również uwzględnić następujące kwestie:  
  
- Jeśli nie ma wiele wywołań między Ewaluator wyrażeń i magazynu symboli lub mogą być odczytywane w magazynie symboli do obszaru pamięci SDM, należy utworzyć DE wewnątrz procesu SDM. Identyfikator CLSID aparat debugowania musi zwrócić SDM, po dołączeniu do programu. SDM używa tego identyfikatora CLSID, do utworzenia wystąpienia w trakcie DE.  
  
- Jeśli DE musi wywołać program, który ma dostęp do magazynu symboli, należy utworzyć DE w procesie z programem. W takim przypadku program tworzy wystąpienie DE.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
