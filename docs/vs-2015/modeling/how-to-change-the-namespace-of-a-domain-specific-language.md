---
title: 'Instrukcje: Zmienianie przestrzeni nazw języka specyficznego dla domeny | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 57ec75ec116b3b107b01a139621d3c59ca8ecac9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094914"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Instrukcje: Zmienianie przestrzeni nazw języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić przestrzeni nazw języka specyficznego dla domeny. Należy wprowadzić zmianę w **Eksplorator DSL**, we właściwościach projektu Dsl pakietu oraz informacje o zestawie.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Aby zmienić przestrzeni nazw języka specyficznego dla domeny  
  
1. W **Eksplorator DSL**, kliknij przycisk **Dsl** węzła.  
  
2. W **właściwości** oknie zmiany **Namespace** właściwości.  
  
3. Zapisywanie rozwiązania i przekształcania szablonów.  
  
4. Na **projektu** menu, kliknij przycisk **właściwości Dsl**.  
  
     Właściwości projektu są wyświetlane.  
  
5. Kliknij przycisk **aplikacji** kartę.  
  
6. Zmiana **domyślny obszar nazw** właściwości na nową nazwę przestrzeni nazw.  
  
7. Jeśli chcesz także zmienić nazwę zestawu, zmień **właściwości nazwy zestawu.**  
  
8. Jeśli zmieniono nazwę zestawu, otwórz DslPackage\Package.tt i zaktualizować ten wiersz:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Jeśli napisano kodu niestandardowego, upewnij się zmienić odwołania do przestrzeni nazw i klasy w plikach kodu.  
  
10. Zresetuj wystąpienie eksperymentalne programu Visual Studio.  
  
    1. Usuń **\Users\\**_{name}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2. Na Windows **Start** menu, wybierz **wszystkie programy**, **Microsoft Visual Studio 2010 SDK**, **narzędzia**, **resetowania Wystąpienie eksperymentalne**.  
  
11. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
