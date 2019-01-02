---
title: Dostawca symboli | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70cd308eaf7234343f7d4c59a7696f668e4415cf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826260"
---
# <a name="symbol-provider"></a>Dostawca symboli
Implementacja ewaluatora wyrażeń musi uzyskać dostęp do symbolicznej informacji debugowania generowanych przez kompilator języka, aby można było Szacowanie zmiennych i wyrażeń. Robi to za korzystanie z interfejsów dostawca symboli (SP), nazywany również obsługi symboli.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza dodatki Service Pack dla kodu zarządzanego, a także kodu macierzystego przy użyciu formatu pliku symboli bazy danych programu (PDB). Chyba że istnieje silna niezbędne do programu za pomocą symboli, przechowywane w niestandardowym formacie, zaleca się używanie dodatki Service Pack, dostarczone przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Uwagi o implementacji  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Silniki debugowania chcą skontaktować się z dodatki Service Pack, przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W rezultacie dodatkiem, który będzie pracował z aparatami debugowania programu Visual Studio musi obsługiwać środowiska CLR. Pełna lista wszystkich CLR profilowanie interfejsów znajduje się w debugref.doc, który jest częścią programu [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Jeśli Twoje SP będzie pracował tylko z Twojego niestandardowego aparatu debugowania, można zaimplementować PS zgodnie z potrzebami w zależności od potrzeb silnik debugowania.  
  
## <a name="see-also"></a>Zobacz także  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)