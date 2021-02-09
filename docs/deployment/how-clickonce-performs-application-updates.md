---
title: Jak technologia ClickOnce wykonuje aktualizacje aplikacji | Microsoft Docs
description: Dowiedz się, w jaki sposób Technologia ClickOnce używa informacji o wersji pliku, aby zdecydować, czy zaktualizować aplikację. Technologia ClickOnce używa poprawek plików, aby uniknąć nadmiarowości podczas pobierania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cdef39a0ab07d4cb9c9f42cf897bd7728934b88d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915741"
---
# <a name="how-clickonce-performs-application-updates"></a>Jak technologia ClickOnce wykonuje aktualizacje aplikacji
ClickOnce używa informacji o wersji pliku określonych w manifeście wdrożenia aplikacji, aby zdecydować, czy zaktualizować pliki aplikacji. Po rozpoczęciu aktualizacji ClickOnce używa techniki o nazwie *poprawka pliku* , aby uniknąć nadmiarowego pobierania plików aplikacji.

## <a name="file-patching"></a>Stosowanie poprawek plików
 Podczas aktualizowania aplikacji ClickOnce nie pobiera wszystkich plików dla nowej wersji aplikacji, o ile pliki nie uległy zmianie. Zamiast tego porównuje sygnatury skrótów plików określonych w manifeście aplikacji dla bieżącej aplikacji względem sygnatur w manifeście dla nowej wersji. Jeśli podpisy pliku różnią się, ClickOnce pobiera nową wersję. Jeśli podpisy są zgodne, plik nie został zmieniony z jednej wersji na następną. W takim przypadku ClickOnce kopiuje istniejący plik i używa go w nowej wersji aplikacji. Takie podejście uniemożliwia programowi ClickOnce pobranie całej aplikacji, nawet jeśli zmieniono tylko jeden lub dwa pliki.

 Poprawka pliku działa również dla zestawów, które są pobierane na żądanie przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metod i.

 Jeśli używasz programu Visual Studio do kompilowania aplikacji, program wygeneruje nowe sygnatury skrótu dla wszystkich plików po odbudowaniu całego projektu. W takim przypadku wszystkie zestawy zostaną pobrane do klienta, mimo że tylko kilka zestawów mogło ulec zmianie.

 Stosowanie poprawek plików nie działa w przypadku plików, które są oznaczone jako dane i przechowywane w katalogu danych. Są one zawsze pobierane niezależnie od sygnatury skrótu pliku. Aby uzyskać więcej informacji na temat katalogu danych, zobacz [dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Zobacz też
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Wybieranie strategii wdrażania technologii ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)