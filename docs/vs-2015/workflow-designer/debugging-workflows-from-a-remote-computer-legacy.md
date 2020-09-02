---
title: Debugowanie przepływów pracy z komputera zdalnego (starsza wersja) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656845"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debugowanie przepływów pracy ze zdalnego komputera (starsza wersja)
W tym temacie opisano sposób debugowania zdalnych starszych [!INCLUDE[wf](../includes/wf-md.md)] aplikacji utworzonych przy użyciu starszej wersji programu [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy aplikacja musi mieć obiekt docelowy [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Podczas instalacji programu [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] jedna z opcji instalacji składników polega na zainstalowaniu [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debugera dla programu [!INCLUDE[wf](../includes/wf-md.md)] . Spowoduje to zainstalowanie składników debugowania zdalnego. Te składniki zdalnego debugowania muszą być zainstalowane na komputerze docelowym dla zdalnego debugowania przepływu pracy.

 Ponadto zestaw zawierający definicję przepływu pracy starszego przepływu pracy, który jest debugowany na komputerze zdalnym, musi być zainstalowany w globalnej pamięci podręcznej zestawów (GAC) na komputerze lokalnym, z którego odbywa się debugowanie. Na przykład jeśli starszy przepływ pracy jest uruchomiony na komputerze zdalnym A i debugowany z komputera lokalnego B, definicja przepływu pracy musi być obecna w pamięci podręcznej komputera B. Dzięki temu Projektant może deserializować i wyświetlić na komputerze B znacznik przepływu pracy, który jest uruchomiony zdalnie na komputerze A. Aby uzyskać więcej informacji na temat globalnej pamięci podręcznej zestawów, zapoznaj się z biblioteką MSDN.

 [!INCLUDE[wf2](../includes/wf2-md.md)] zdalne debugowanie działa tak samo jak debugowanie zdalne dla innych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] składników. Aby uzyskać więcej informacji, zobacz [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] zdalne debugowanie w bibliotece MSDN.

## <a name="see-also"></a>Zobacz też
 [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)