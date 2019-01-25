---
title: 'Instrukcje: Wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4aafc503ff2b8dffed5b70d17f4eb488baf72704
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865089"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Instrukcje: Wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym
  Oprócz wdrażania rozwiązań programu SharePoint do systemu lokalnego, można publikować rozwiązania w trybie piaskownicy programu SharePoint na lokacjach zdalnych i lokalnych witryn programu SharePoint. Zdalnej kopii procesu publikowania *.wsp* pliku na serwerze programu SharePoint, instaluje rozwiązanie i następnie umożliwia aktywację rozwiązania. Możesz również uaktualnić zdalnej instalacji rozwiązania programu SharePoint, po wprowadzeniu zmian do niego.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Aby opublikować rozwiązanie w trybie piaskownicy programu SharePoint na serwerze zdalnym programu SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla piaskownicy projektu programu SharePoint, który chcesz opublikować, a następnie wybierz **Publikuj**.  
  
2.  W **Publikuj** okna dialogowego wybierz **publikowania w witrynie SharePoint** przycisk opcji, a następnie wprowadź adres URL witryny do publikowania online, takich jak: `https://mytestsite.sharepoint.microsoftonline.com`.  
  
3.  Wybierz **Otwórz stronę Galeria rozwiązań w przeglądarce po opublikowaniu** przycisk opcji, aby wyświetlić listę rozwiązań w **Galeria rozwiązań** strony po opublikowaniu.  
  
4.  Wybierz **Publikuj** przycisku.  
  
5.  Zaloguj się do serwera zdalnego, jeśli wymagane jest uwierzytelnienie użytkownika.  
  
     Publikowanie postępu jest wyświetlana w programie Visual Studio **dane wyjściowe** okna. Po zakończeniu procesu rozwiązania (*.wsp*) pliku jest zainstalowany na zdalnym serwerze programu SharePoint. Jednak go nadal należy aktywować zanim będzie można używać w programie SharePoint.  
  
6.  Na **Galeria rozwiązań** stronie, wybierz aplikację programu SharePoint, a następnie na Wstążce, wybierz **Aktywuj** przycisku.  
  
7.  W **Aktywowanie rozwiązania** okno dialogowe, na Wstążce, wybierz **Aktywuj** ponownie przycisk.  
  
     **Stan** kolumny na **Galeria rozwiązań** strona wskazuje, że aplikacja jest aktywna.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Aby uaktualnić rozwiązanie w trybie piaskownicy programu SharePoint na zdalnym serwerze programu SharePoint  
 Jeśli rozwiązanie w trybie piaskownicy programu SharePoint został już opublikowany na serwerze zdalnym, następujący proces pozwala na uaktualnianie go po wprowadzeniu zmian do aplikacji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Zmień nazwę pakietu programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby to zrobić, w **Eksploratora rozwiązań** Otwórz pakiet. Zostanie on wyświetlony na **narzędziu Package Explorer**.  
  
2.  W **narzędziu Package Explorer**w **nazwa** pola, Zmień nazwę pakietu na unikatową nazwę.  
  
3.  Zapisz projekt.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **Publikuj**.  
  
5.  W **Publikuj** okna dialogowego wybierz **publikowania w witrynie SharePoint** przycisk opcji, a następnie, jeśli brakuje adresu URL dla serwera zdalnego, w którym rozwiązanie jest zapisywana, wprowadź go.  
  
6.  Wybierz **Otwórz stronę Galeria rozwiązań w przeglądarce po opublikowaniu** przycisk opcji, aby wyświetlić listę rozwiązań w **Galeria rozwiązań** strony po opublikowaniu.  
  
7.  Wybierz **Publikuj** przycisku.  
  
8.  Zaloguj się do serwera zdalnego, jeśli wymagane jest uwierzytelnienie użytkownika.  
  
     Jeśli użytkownik zalogował się do serwera zdalnego niedawno, uwierzytelniania nie może być wymagane.  
  
     Jeśli starszą wersję aplikacji, która ma taką samą nazwę, która jest nadal istnieje na serwerze programu SharePoint, zostanie wyświetlony błąd, który pakiet o tej samej nazwie już istnieje na serwerze programu SharePoint. Należy zmienić nazwę pakietu na unikatową nazwę, przed opublikowaniem.  
  
9. Wybierz nową aplikację w programie SharePoint, a następnie na Wstążce, wybierz **uaktualnienia** przycisku.  
  
10. W **Uaktualnij rozwiązanie** okno dialogowe, na Wstążce, wybierz **uaktualnienia** ponownie przycisk. **Stan** kolumny na **Galeria rozwiązań** strony powinny teraz wskazywać, że aplikacja jest aktywna.  
  
     Dezaktywacji starą wersję rozwiązania, nowa wersja rozwiązania jest uaktualniany razem z danych zachowywanych ze starego rozwiązania, a nowe rozwiązanie jest aktywna w programie SharePoint.  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
