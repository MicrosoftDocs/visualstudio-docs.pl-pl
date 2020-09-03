---
title: Wdrożenie powłoki VS Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659302"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Izolowana Powłoka pozwala określić, które funkcje programu Visual Studio mają być używane w celu współdziałania z językiem specyficznym dla domeny oraz jak ma wyglądać to rozwiązanie. Aby uzyskać więcej informacji na temat izolowanej powłoki programu Visual Studio, zobacz [Dostosowywanie powłoki izolowanej](../extensibility/customizing-the-isolated-shell.md). Więcej informacji na temat dostosowywania izolowanej powłoki można znaleźć w temacie [Dostosowywanie powłoki izolowanej](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Aby ustawić program Visual Studio Shell jako element docelowy wdrożenia

1. W projekcie **DslPackage** Otwórz **source.Extension.tt**.

2. W obszarze `<SupportedProducts>` Wstaw:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Zastąp *MyIsolatedShell* nazwą pakietu izolowanej powłoki.
