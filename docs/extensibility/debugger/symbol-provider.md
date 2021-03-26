---
title: Dostawca symboli | Microsoft Docs
description: Zapoznaj się z dostawcami symboli dostarczanymi przez program Visual Studio, aby umożliwić ewaluatora wyrażeń Obliczanie zmiennych i wyrażeń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 132e3c15eed86c9008e49b74b6da6e5da5a3ce33
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079387"
---
# <a name="symbol-provider"></a>Dostawca symboli
Implementacja ewaluatora wyrażeń musi uzyskać dostęp do symbolicznych informacji debugowania generowanych przez kompilator języka w celu obliczenia zmiennych i wyrażeń. Robi to poprzez zużywanie interfejsów dostawcy symboli (SP), nazywanych również obsługą symboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza program SPs dla kodu zarządzanego oraz kod natywny przy użyciu formatu pliku symboli bazy danych (PDB). Jeśli program nie ma silnej potrzeby używania symboli przechowywanych w formacie niestandardowym, zaleca się korzystanie z programu SPs dostarczonego przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Uwagi o implementacji
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Aparaty debugowania oczekują na rozmowę z programem SPS przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym, SP, który będzie pracował z aparatami debugowania programu Visual Studio, musi obsługiwać środowisko CLR. Pełną listę interfejsów debugowania CLR można znaleźć w debugref.doc, która jest częścią [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Jeśli program SP będzie działał tylko z niestandardowym aparatem debugowania, można zaimplementować program SP w zależności od potrzeb aparatu debugowania.

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
