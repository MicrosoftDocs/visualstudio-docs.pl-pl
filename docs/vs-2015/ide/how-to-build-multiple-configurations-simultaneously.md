---
title: 'Instrukcje: Równoczesne kompilowanie wielu konfiguracji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 431978a10081ec50e9eaca7e88a37f1447f953e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785871"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Instrukcje: Równoczesne kompilowanie wielu konfiguracji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Większość typów projektów z wieloma lub nawet wszystkich ich konfiguracje kompilacji, w tym samym czasie można tworzyć przy użyciu **tworzenie partii** okno dialogowe. Jednak nie można utworzyć następujące typy projektów w wielu konfiguracjach kompilacji, w tym samym czasie:  
  
1. [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje są kompilowane dla Windows przy użyciu języka JavaScript.  
  
2. Wszystkie projekty języka Visual Basic.  
  
   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md).  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby skompilować projekt w wielu konfiguracjach kompilacji  
  
1.  Na pasku menu wybierz **kompilacji**, **tworzenie partii**.  
  
2.  W **kompilacji** kolumny, zaznacz pola wyboru dla konfiguracji, w których chcesz utworzyć projekt.  
  
    > [!TIP]
    >  Aby edytować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz opcję **kompilacji**, **programu Configuration Manager** na pasku menu, aby otworzyć **programu Configuration Manager** okno dialogowe. Po zakończeniu edycji konfigurację kompilacji dla rozwiązania, wybierz **odbudować** znajdujący się w **tworzenie partii** okno dialogowe, aby zaktualizować wszystkie kompilowanie konfiguracji dla projektów w rozwiązaniu.  
  
3.  Wybierz **kompilacji** lub **odbudować** przycisków, aby skompilować projekt z konfiguracjami, które można określić.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)   
 [Ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md)   
 [Równoległe tworzenie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
