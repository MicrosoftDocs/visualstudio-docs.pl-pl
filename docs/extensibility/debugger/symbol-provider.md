---
title: Dostawca symboli | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712819"
---
# <a name="symbol-provider"></a>Dostawca symboli
Implementacja oceniająca wyrażenie musi uzyskać dostęp do symbolicznych informacji debugowania generowanych przez kompilator języka w celu oceny zmiennych i wyrażeń. Robi to przez użycie interfejsów dostawcy symbolu (SP), zwanego również programem obsługi symboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dostarcza SPs dla kodu zarządzanego, a także kodu macierzystego przy użyciu formatu pliku symbolu Programu DataBase (PDB). O ile program nie potrzebuje silnego zapotrzebowania na symbole przechowywane w formacie niestandardowym, zaleca [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]się używanie adresów SPs dostarczonych przez program .

## <a name="implementation-notes"></a>Uwagi o implementacji
 Aparaty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania oczekiwać, aby porozmawiać z SPs przy użyciu interfejsów wspólnego środowiska wykonawczego języka (CLR). W rezultacie SP, który będzie współpracować z aparatami debugowania programu Visual Studio musi obsługiwać CLR. Pełną listę wszystkich interfejsów debugowania CLR można znaleźć w pliku debugref.doc, który jest częścią [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]pliku .

 Jeśli sp będzie działać tylko z aparatem debugowania niestandardowe, można zaimplementować SP, jak na to zgodzie w zależności od potrzeb aparatu debugowania.

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
