---
title: Tworzenie rozszerzenia za pomocą okna narzędzia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118126"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej procedurze opisano sposób użyć szablonu projektu VSIX i **okna narzędzi niestandardowych** szablonu elementu Tworzenie rozszerzenia za pomocą okna narzędzi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Tworzenie okna narzędzi  
  
1. Utwórz projekt VSIX, o nazwie **FirstWindow**. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2. Po otwarciu projektu, należy dodać szablon elementu okno narzędzia o nazwie **FirstWindow**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **okna narzędzi niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku okna narzędzi, aby **FirstWindow.cs**.  
  
3. Skompiluj projekt, a następnie rozpocząć debugowanie.  
  
     Pojawi się doświadczalnym wystąpieniu programu Visual Studio. Aby uzyskać więcej informacji na temat wystąpienia eksperymentalnego zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).  
  
4. W doświadczalnym wystąpieniu, przejdź do **widok / inne Windows**.  
  
     Powinien zostać wyświetlony element menu dla **FirstWindow**. Kliknij go.  
  
     Powinien zostać wyświetlony okna narzędzi z tytułem **FirstWindow** i powiedzenie przycisk **kliknij mnie!.**
