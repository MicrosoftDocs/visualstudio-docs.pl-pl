---
title: Zdalne wdrażanie, publikowanie & Uaktualnianie rozwiązań SharePoint
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f05f42f8aed35696b962e71a5fce86c2956b3661
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016809"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Instrukcje: wdrażanie, publikowanie i uaktualnianie rozwiązań SharePoint na serwerze zdalnym
  Oprócz wdrażania rozwiązań programu SharePoint w systemie lokalnym można publikować rozwiązania programu SharePoint w trybie piaskownicy w witrynach zdalnych lub lokalnych witrynach programu SharePoint. Proces publikowania zdalnego kopiuje plik *. wsp* do serwera programu SharePoint, instaluje rozwiązanie, a następnie umożliwia aktywowanie rozwiązania. Możesz również uaktualnić zdalną instalację rozwiązania SharePoint po wprowadzeniu zmian.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Aby opublikować rozwiązanie SharePoint w trybie piaskownicy na zdalnym serwerze programu SharePoint

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu programu SharePoint w trybie piaskownicy, który chcesz opublikować, a następnie wybierz polecenie **Publikuj**.

2. W oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w witrynie SharePoint** , a następnie wprowadź adres URL dla witryny publikacji online, na przykład: `https://mytestsite.sharepoint.microsoftonline.com` .

3. Aby wyświetlić listę rozwiązań na stronie **galerii rozwiązań** po opublikowaniu, wybierz **stronę Otwórz galerię rozwiązań w przeglądarce po opublikowaniu** przycisku opcji.

4. Wybierz przycisk **Publikuj** .

5. Zaloguj się na serwerze zdalnym, jeśli wymagane jest uwierzytelnianie użytkownika.

     Postęp publikowania pojawia się w oknie **danych wyjściowych** programu Visual Studio. Po zakończeniu procesu na zdalnym serwerze programu SharePoint jest instalowany plik rozwiązania (*wsp*). Jednak nadal musi być aktywowany, zanim będzie można go używać w programie SharePoint.

6. Na stronie **Galeria rozwiązań** wybierz aplikację SharePoint, a następnie na wstążce wybierz przycisk **Aktywuj** .

7. W oknie dialogowym **Aktywuj rozwiązanie** na wstążce wybierz ponownie przycisk **Aktywuj** .

     Kolumna **stan** na stronie **Galeria rozwiązań** wskazuje, że aplikacja jest aktywna.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Aby uaktualnić rozwiązanie programu SharePoint w trybie piaskownicy na zdalnym serwerze programu SharePoint
 Jeśli rozwiązanie programu SharePoint w trybie piaskownicy jest już opublikowane na serwerze zdalnym, poniższy proces umożliwia uaktualnienie go po wprowadzeniu zmian w aplikacji w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Zmień nazwę pakietu programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . W tym celu w **Eksplorator rozwiązań** otworzyć pakiet. Jest on wyświetlany w **Eksploratorze pakietów**.

2. W **Eksploratorze pakietów**w polu **Nazwa** Zmień nazwę pakietu na unikatową.

3. Zapisz projekt.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Publikuj**.

5. W oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w witrynie programu SharePoint** , a następnie, jeśli brakuje adresu URL serwera zdalnego, na którym zapisano rozwiązanie, wprowadź je.

6. Aby wyświetlić listę rozwiązań na stronie **galerii rozwiązań** po opublikowaniu, wybierz **stronę Otwórz galerię rozwiązań w przeglądarce po opublikowaniu** przycisku opcji.

7. Wybierz przycisk **Publikuj** .

8. Zaloguj się na serwerze zdalnym, jeśli wymagane jest uwierzytelnianie użytkownika.

     Jeśli ostatnio zalogowano się na serwerze zdalnym, uwierzytelnianie może nie być wymagane.

     Jeśli starsza wersja aplikacji, która ma taką samą nazwę, nadal istnieje na serwerze programu SharePoint, zostanie wyświetlony komunikat o błędzie, że pakiet o tej samej nazwie już istnieje na serwerze programu SharePoint. Przed opublikowaniem należy zmienić nazwę pakietu na unikatową.

9. Wybierz nową aplikację w programie SharePoint, a następnie na wstążce wybierz przycisk **Uaktualnij** .

10. W oknie dialogowym **uaktualnienie rozwiązania** na wstążce wybierz ponownie przycisk **Uaktualnij** . Kolumna **stan** na stronie **Galeria rozwiązań** powinna teraz wskazywać, że aplikacja jest aktywna.

     Stara wersja rozwiązania została zdezaktywowana, Nowa wersja rozwiązania zostanie uaktualniona przy użyciu danych przechowywanych ze starego rozwiązania, a nowe rozwiązanie zostanie aktywowane w programie SharePoint.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: wdrażanie i publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
