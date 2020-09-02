---
title: Wprowadzenie z rozszerzalnością debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152699"
---
# <a name="getting-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Zawiera informacje, które należy wykonać, aby utworzyć i dostosować składniki debugera używane do debugowania programów z poziomu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugowanie dodaliśmy ulepszenia wynikające z rozbudowanych testów użyteczności wykonanych na wcześniejszych [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugerach. Debugowania można użyć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do przechodzenia przez aplikację z obsługą wielu języków lub podczas debugowania aplikacji i rozwiązań wielojęzycznych.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugowanie jest wykonywane poza procesem z debugowanym programem i w związku z tym jest mniej niepożądane w przestrzeni procesu aplikacji. W związku z tym łatwiej jest pisać składniki, które współdziałają z debugerem bez wpływu na program do debugowania.  
  
 Aby najlepiej korzystać z programu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , należy zapoznać się z następującymi kwestiami:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Zintegrowane środowisko programistyczne (IDE)  
  
- Język programowania C++  
  
- ATL COM  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Plan rozwoju rozszerzania debugera](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Przedstawia proces implementowania debugowania w produkcie, w zależności od kompilatora i jego danych wyjściowych.  
  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] składników debugowania, takich jak aparat debugowania (de), ewaluatora wyrażeń (EE) i procedura obsługi symboli (SH).  
  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 Opisuje główne koncepcje dotyczące architektury debugowania.  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 Wyjaśnia, w jaki sposób aparat debugowania (DE) działa jednocześnie w kontekście kodu, dokumentacji oraz kontekstów oceny wyrażenia. Opisuje, dla każdego z trzech kontekstów, lokalizacji, pozycji lub oceny, które są dla niego odpowiednie.  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.
