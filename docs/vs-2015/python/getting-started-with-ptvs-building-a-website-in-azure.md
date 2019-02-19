---
title: 'Wprowadzenie do narzędzi PTVS: Tworzenie witryny sieci Web na platformie Azure | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 61f8748a3874f32db9c235d03b6b7464bc5cecf1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783199"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Wprowadzenie do narzędzi PTVS: Tworzenie witryny sieci Web na platformie Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz rozpocząć szybkiego tworzenia witryny sieci web języka Python na platformie Azure.  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Rozpocznij przy użyciu nowego projektu... okno dialogowe i w obszarze Python projektów, wybierz projekt sieci Web Bottle.  To [Bottle](http://bottlepy.org/docs/dev/index.html) jest szablon witryny początkowej, na podstawie [Bootstrap framework](http://getbootstrap.com/).  Podczas tworzenia projektu w programie Visual Studio zostanie wyświetlony monit o zainstalowanie zależności (Bottle, w tym przypadku) w środowisku wirtualnym.  Ponieważ jest wdrażany na witrynę sieci Web platformy Azure, należy dodać zależności do środowiska wirtualnego w celu wdrożenia konieczne bitów dla operacji witryny.  Należy również podstawą środowiska Python 2.7 lub 3.4 32-bitowych.  Po utworzeniu projektu, naciśnij klawisz F5, aby rozpocząć uruchamianie witryny lokalnie.  
  
 Jest łatwy do wypróbowania witryny na platformie Azure.  Jeśli nie masz subskrypcji platformy Azure, możesz użyć [try.azurewebsites.net](https://trywebsites.azurewebsites.net/).  Ta witryna oferuje prosty sposób na wypróbowanie usługi Azure Websites na godzinę naraz tylko logowania z serwisów społecznościowych.  Karta kredytowa nie jest konieczne.  Wybieranie szablonu pustej witryny na liście rozwijanej pola Zmień język i wybierz polecenie Utwórz.  W obszarze "Praca z aplikacją sieci web" wybierz pozycję Pobierz profil publikowania, a następnie zapisz plik do użytku z programem Visual Studio.  Można również wdrożyć przy użyciu narzędzia git z dowolnego systemu operacyjnego.  
  
 Przełącz z powrotem w programie Visual Studio i projekt, który został utworzony.  Wybierz węzeł projektu w Eksploratorze rozwiązań, wybierz przycisk prawo wskaźnika i wybierz polecenie Publikuj.  Jeśli masz subskrypcję platformy Azure, możesz kliknąć w witrynach sieci Web Microsoft Azure, w oknie dialogowym Zarządzanie lokacje, w tym miejscu.  W ramach tego przewodnika wybierz opcję Importuj, aby zaimportować profil publikowania, który został pobrany.  Ponieważ profil publikowania zawiera wszystkie niezbędne informacje, możesz wybrać publikowania.  W ciągu kilku sekund zostanie otwarte nowe okno przeglądarki, a lokacja jest na żywo hostowanych w chmurze platformy Azure.  
  
 Proste witryn sieci Web są łatwe, ale aby uzyskać informacje dotyczące bardziej znaczące aplikacji sieci web na platformie Azure, zobacz [zagłębia](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) wideo oraz innych użytkowników w tym kanale (link w prawym górnym rogu strony pobierania uruchomiona lub deep dive wideo, a także poniżej .  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja witryny typu wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [Wprowadzenie rozpoczęcie pracy i Deep Dive wideo narzędzi PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
