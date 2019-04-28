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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea31d6bcd8c055756a49c46f8fb4b3f377aaade8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912901"
---
# <a name="symbol-provider"></a>Dostawca symboli
Implementacja ewaluatora wyrażeń musi uzyskać dostęp do symbolicznej informacji debugowania generowanych przez kompilator języka, aby można było Szacowanie zmiennych i wyrażeń. Robi to za korzystanie z interfejsów dostawca symboli (SP), nazywany również obsługi symboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza dodatki Service Pack dla kodu zarządzanego, a także kodu macierzystego przy użyciu formatu pliku symboli bazy danych programu (PDB). Chyba że istnieje silna niezbędne do programu za pomocą symboli, przechowywane w niestandardowym formacie, zaleca się używanie dodatki Service Pack, dostarczone przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="implementation-notes"></a>Uwagi o implementacji
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Silniki debugowania chcą skontaktować się z dodatki Service Pack, przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W rezultacie dodatkiem, który będzie pracował z aparatami debugowania programu Visual Studio musi obsługiwać środowiska CLR. Pełna lista wszystkich CLR profilowanie interfejsów znajduje się w debugref.doc, który jest częścią programu [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Jeśli Twoje SP będzie pracował tylko z Twojego niestandardowego aparatu debugowania, można zaimplementować PS zgodnie z potrzebami w zależności od potrzeb silnik debugowania.

## <a name="see-also"></a>Zobacz także
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)