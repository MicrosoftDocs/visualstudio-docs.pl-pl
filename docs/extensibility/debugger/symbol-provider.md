---
title: Dostawca symboli | Microsoft Docs
description: Dowiedz się więcej o dostawcach symboli, Visual Studio dostarcza, aby umożliwić ewaluatorowi wyrażeń ocenę zmiennych i wyrażeń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3332bbf705d8e3149d864dbb35418fd4c12c523b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902920"
---
# <a name="symbol-provider"></a>Dostawca symboli
Implementacja ewaluatora wyrażeń musi uzyskać dostęp do symbolicznych informacji debugowania generowanych przez kompilator języka w celu oceny zmiennych i wyrażeń. Robi to przez korzystanie z interfejsów dostawcy symboli (SP), nazywanego również programem obsługi symboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dostarcza SPs dla kodu zarządzanego, a także kod natywny przy użyciu formatu pliku symboli Programu DataBase (PDB). Jeśli program nie ma silnej potrzeby używania symboli przechowywanych w niestandardowym formacie, zaleca się użycie opcji SPs dostarczonych przez program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Uwagi o implementacji
 Aparaty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania oczekują, że będą rozmawiać z programami SPs przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym sp, która będzie pracować z aparatami debugowania Visual Studio musi obsługiwać clr. Pełną listę wszystkich interfejsów debugowania CLR można znaleźć w debugref.doc, który jest częścią [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Jeśli twój sp z o.o. będzie działać tylko z niestandardowym aparatem debugowania, możesz zaimplementować sp w zależności od potrzeb aparatu debugowania.

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
