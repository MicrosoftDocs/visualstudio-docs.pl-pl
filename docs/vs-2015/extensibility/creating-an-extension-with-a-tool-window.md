---
title: Tworzenie rozszerzenia za pomocą okna narzędzia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431852"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej procedurze dowiesz się, jak używać szablonu projektu VSIX i szablonu elementu **okna narzędzia niestandardowego** do tworzenia rozszerzenia przy użyciu okna narzędzi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Tworzenie okna narzędzi  
  
1. Utwórz projekt VSIX o nazwie **FirstWindow**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C#/rozszerzalność**.  
  
2. Po otwarciu projektu Dodaj szablon elementu okna narzędzia o nazwie **FirstWindow**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do pozycji **Visual C#/rozszerzalność** i wybierz **niestandardowe okno narzędzi**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku okna narzędzia na **FirstWindow.cs**.  
  
3. Skompiluj projekt i Rozpocznij debugowanie.  
  
     Pojawia się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji o wystąpieniu eksperymentalnym, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).  
  
4. W eksperymentalnym wystąpieniu przejdź do **widoku/innych okien**.  
  
     Powinien zostać wyświetlony element menu dla **FirstWindow**. Kliknij go.  
  
     Powinno zostać wyświetlone okno narzędzi z tytułem **FirstWindow** i przyciskiem mówiącym **kliknij mnie!.**
