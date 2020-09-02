---
title: Jak technologia ClickOnce wykonuje aktualizacje aplikacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2e8a3c1054219bb7d5b0f9a9ef5e710786344e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152832"
---
# <a name="how-clickonce-performs-application-updates"></a>Jak technologia ClickOnce wykonuje aktualizacje aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce używa informacji o wersji pliku określonych w manifeście wdrożenia aplikacji, aby zdecydować, czy zaktualizować pliki aplikacji. Po rozpoczęciu aktualizacji ClickOnce używa techniki o nazwie *poprawka pliku* , aby uniknąć nadmiarowego pobierania plików aplikacji.  
  
## <a name="file-patching"></a>Stosowanie poprawek plików  
 Podczas aktualizowania aplikacji ClickOnce nie pobiera wszystkich plików dla nowej wersji aplikacji, o ile pliki nie uległy zmianie. Zamiast tego porównuje sygnatury skrótów plików określonych w manifeście aplikacji dla bieżącej aplikacji względem sygnatur w manifeście dla nowej wersji. Jeśli podpisy pliku różnią się, ClickOnce pobiera nową wersję. Jeśli podpisy są zgodne, plik nie został zmieniony z jednej wersji na następną. W takim przypadku ClickOnce kopiuje istniejący plik i używa go w nowej wersji aplikacji. Takie podejście uniemożliwia programowi ClickOnce pobranie całej aplikacji, nawet jeśli zmieniono tylko jeden lub dwa pliki.  
  
 Poprawka pliku działa również dla zestawów, które są pobierane na żądanie przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metod i.  
  
 Jeśli używasz programu Visual Studio do kompilowania aplikacji, program wygeneruje nowe sygnatury skrótu dla wszystkich plików po odbudowaniu całego projektu. W takim przypadku wszystkie zestawy zostaną pobrane do klienta, mimo że tylko kilka zestawów mogło ulec zmianie.  
  
 Stosowanie poprawek plików nie działa w przypadku plików, które są oznaczone jako dane i przechowywane w katalogu danych. Są one zawsze pobierane niezależnie od sygnatury skrótu pliku. Aby uzyskać więcej informacji na temat katalogu danych, zobacz [dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
