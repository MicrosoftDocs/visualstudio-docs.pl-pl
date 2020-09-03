---
title: 'Wprowadzenie z PTVS: kompilowanie witryny sieci Web na platformie Azure | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 288fb24c9c1c4ddee1cb59a968e717531e274af1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300585"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Pierwsze kroki z narzędziami PTVS: tworzenie witryny sieci Web na platformie Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz szybko rozpocząć tworzenie witryny sieci Web w języku Python na platformie Azure.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)w serwisie YouTube.  
  
 Rozpocznij od nowego projektu... w oknie dialogowym i w obszarze projekty języka Python wybierz projekt sieci Web z butelką.  Ten szablon [butelek](http://bottlepy.org/docs/dev/index.html) jest lokacją startową opartą na [strukturze Bootstrap](https://getbootstrap.com/).  Podczas tworzenia projektu program Visual Studio poprosi o zainstalowanie zależności (butelk w tym przypadku) w środowisku wirtualnym.  Ponieważ wdrażasz w witrynie sieci Web platformy Azure, musisz dodać zależności do środowiska wirtualnego, aby wdrożyć niezbędne bity dla operacji witryny.  Konieczne jest również oparcie środowiska w języku Python 2,7 lub 3,4 32-bit.  Po utworzeniu projektu naciśnij klawisz F5, aby rozpocząć Uruchamianie lokacji lokalnie.  
  
 Wypróbowanie witryny na platformie Azure jest łatwe.  Jeśli nie masz subskrypcji platformy Azure, możesz użyć [try.azurewebsites.NET](https://trywebsites.azurewebsites.net/).  Ta witryna oferuje prosty sposób wypróbowania usługi Azure Websites na godzinę w danym momencie przy użyciu tylko nazwy logowania w społeczności.  Karta kredytowa nie jest potrzebna.  Wybierz pusty szablon witryny na liście rozwijanej Zmień język i wybierz pozycję Utwórz.  W obszarze "Pracuj z aplikacją sieci Web" Wybierz pozycję Pobierz profil publikowania i Zapisz plik do użycia z programem Visual Studio.  Można również wdrożyć przy użyciu narzędzia Git z dowolnego systemu operacyjnego.  
  
 Przełącz się z powrotem do programu Visual Studio i utworzonego projektu.  Wybierz węzeł projektu w Eksplorator rozwiązań, wybierz przycisk prawy wskaźnik i wybierz polecenie Publikuj.  Jeśli masz subskrypcję platformy Azure, możesz kliknąć pozycję Microsoft Azure Websites w oknie dialogowym, aby zarządzać witrynami w tym miejscu.  Na potrzeby tego przewodnika wybierz pozycję Importuj, aby zaimportować właśnie pobrany profil publikowania.  Ponieważ profil publikowania zawiera wszystkie niezbędne informacje, możesz wybrać pozycję Publikuj.  W ciągu kilku sekund zostanie otwarte nowe okno przeglądarki, a witryna będzie hostowana w chmurze platformy Azure.  
  
 Proste witryny sieci Web są proste, ale aby uzyskać informacje na temat bardziej znaczących aplikacji sieci Web na platformie Azure, zobacz [głębokie wideo szczegółowe](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) , a także inne w tym kanale (link w prawym górnym rogu strony pobieranie lub głębokie szczegółowe wideo), jak również poniżej.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)w serwisie YouTube.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja typu wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [PTVS Wprowadzenie i głębokie wideo szczegółowe](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
