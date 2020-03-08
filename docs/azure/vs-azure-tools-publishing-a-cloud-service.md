---
title: Publikowanie usługi w chmurze przy użyciu narzędzi platformy Azure | Microsoft Docs
description: Dowiedz się, jak publikować projekty usług w chmurze platformy Azure za pomocą programu Visual Studio.
author: ghogen
manager: jillfra
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: d8257e0833da470554ce331c30cd0edf74122093
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408688"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publikowanie usługi w chmurze za pomocą programu Visual Studio

Program Visual Studio może publikować aplikację bezpośrednio na platformie Azure z obsługą środowiska przejściowego i produkcyjnego w ramach usługi w chmurze. Podczas publikowania należy wybrać środowisko wdrażania i konto magazynu, które jest tymczasowo używane dla pakietu wdrożeniowego.

Podczas tworzenia i testowania aplikacji platformy Azure można użyć Web Deploy, aby publikować zmiany przyrostowo dla ról sieci Web. Po opublikowaniu aplikacji w środowisku wdrażania Web Deploy umożliwia wdrożenie zmian bezpośrednio na maszynie wirtualnej, na której działa rola sieci Web. Nie ma potrzeby pakowania i publikowania całej aplikacji platformy Azure za każdym razem, gdy chcesz zaktualizować rolę sieci Web w celu przetestowania zmian. Dzięki temu można mieć dostęp do roli sieci Web w chmurze na potrzeby testowania bez czekania na opublikowanie aplikacji w środowisku wdrożenia.

Użyj następujących procedur, aby opublikować aplikację platformy Azure i zaktualizować rolę sieci Web przy użyciu Web Deploy:

- Publikowanie lub pakowanie aplikacji platformy Azure z poziomu programu Visual Studio
- Aktualizowanie roli sieci Web w ramach cyklu tworzenia i testowania

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publikowanie lub pakowanie aplikacji platformy Azure z poziomu programu Visual Studio

Po opublikowaniu aplikacji platformy Azure można wykonać jedną z następujących czynności:

- Utwórz pakiet usługi: można użyć tego pakietu i pliku konfiguracji usługi do opublikowania aplikacji w środowisku wdrażania z [Azure Portal](https://portal.azure.com).

- Opublikuj projekt platformy Azure z poziomu programu Visual Studio: Aby opublikować aplikację bezpośrednio na platformie Azure, użyj Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [Kreator publikowania aplikacji platformy Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Aby utworzyć pakiet usługi z programu Visual Studio

1. Gdy wszystko będzie gotowe do opublikowania aplikacji, Otwórz Eksplorator rozwiązań, otwórz menu skrótów dla projektu platformy Azure, który zawiera Twoje role, a następnie wybierz polecenie Publikuj.

1. Aby utworzyć tylko pakiet usługi, wykonaj następujące kroki:

   a. W menu skrótów dla projektu platformy Azure wybierz pozycję **pakiet**.

   b. W oknie dialogowym **pakowanie aplikacji platformy Azure** wybierz konfigurację usługi, dla której chcesz utworzyć pakiet, a następnie wybierz konfigurację kompilacji.

   c. Obowiązkowe Aby włączyć Pulpit zdalny dla usługi w chmurze po jej opublikowaniu, wybierz pozycję **włącz pulpit zdalny dla wszystkich ról**, a następnie wybierz pozycję **Ustawienia** , aby skonfigurować pulpit zdalny poświadczenia. Aby uzyskać więcej informacji, zobacz [włączanie Podłączanie pulpitu zdalnego dla roli na platformie Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Jeśli chcesz debugować usługę w chmurze po jej opublikowaniu, Włącz debugowanie zdalne, wybierając opcję **Włącz debuger zdalny dla wszystkich ról**.

   d. Aby utworzyć pakiet, wybierz link **pakiet** .

      Eksplorator plików pokazuje lokalizację pliku nowo utworzonego pakietu. Możesz skopiować tę lokalizację, aby można było jej używać z poziomu Azure Portal.

   e. Aby opublikować ten pakiet w środowisku wdrażania, należy użyć tej lokalizacji jako lokalizacji pakietu podczas tworzenia usługi w chmurze i wdrożyć ten pakiet w środowisku z Azure Portal.

1. Obowiązkowe Aby anulować proces wdrażania, w menu skrótów dla elementu wiersza w dzienniku aktywności wybierz polecenie **Anuluj i Usuń**. To polecenie powoduje zatrzymanie procesu wdrażania i usuwa środowisko wdrażania na platformie Azure. Aby usunąć środowisko po wdrożeniu, użyj Azure Portal.

1. Obowiązkowe Po rozpoczęciu wystąpień roli program Visual Studio automatycznie wyświetli środowisko wdrożenia w węźle **Cloud Services** w Eksplorator serwera. W tym miejscu można zobaczyć stan poszczególnych wystąpień ról. Zobacz [Zarządzanie zasobami platformy Azure za pomocą programu Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md). Na poniższej ilustracji przedstawiono wystąpienia roli, podczas gdy nadal są w stanie inicjowania:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Aktualizowanie roli sieci Web w ramach cyklu tworzenia i testowania

Jeśli infrastruktura zaplecza aplikacji jest stabilna, ale role sieci Web potrzebują coraz częściej aktualizacji, można użyć Web Deploy, aby zaktualizować tylko rolę sieci Web w projekcie. Web Deploy jest przydatny, gdy nie chcesz odbudować i ponownie wdrożyć ról procesu roboczego zaplecza, lub jeśli masz wiele ról sieci Web i chcesz zaktualizować tylko jedną z ról sieci Web.

### <a name="requirements-for-using-web-deploy"></a>Wymagania dotyczące używania Web Deploy

- **Tylko do celów deweloperskich i testowych**: zmiany są wprowadzane bezpośrednio do maszyny wirtualnej, w której uruchomiono rolę sieci Web. Jeśli ta maszyna wirtualna musi zostać odtworzona, zmiany zostaną utracone, ponieważ oryginalny opublikowany pakiet jest używany do odtworzenia maszyny wirtualnej dla tej roli. Opublikuj ponownie aplikację, aby uzyskać najnowsze zmiany roli sieci Web.

- **Można aktualizować tylko role sieci Web**: nie można zaktualizować ról procesu roboczego. Ponadto nie można zaktualizować `RoleEntryPoint` w `web role.cs`.

- **Może obsługiwać tylko pojedyncze wystąpienie roli sieci Web**: w środowisku wdrażania nie można mieć wielu wystąpień żadnej roli sieci Web. Jednak obsługiwane są wiele ról sieci Web z tylko jednym wystąpieniem.

- **Włącz połączenia pulpitu zdalnego**: to wymaganie umożliwia Web Deploy do łączenia się z maszyną wirtualną przy użyciu użytkownika i hasła w celu wdrożenia zmian na serwerze z uruchomionym programem Internet Information Services (IIS). Ponadto może być konieczne nawiązanie połączenia z maszyną wirtualną w celu dodania certyfikatu zaufanego do usług IIS na tej maszynie wirtualnej. (Ten certyfikat gwarantuje, że połączenie zdalne dla usług IIS, które jest używane przez Web Deploy jest bezpieczne.)

W poniższej procedurze przyjęto założenie, że używasz kreatora **publikacji aplikacji platformy Azure** .

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Włącz Web Deploy podczas publikowania aplikacji

1. Aby włączyć opcję **włącz Web Deploy dla wszystkich ról sieci Web** , należy najpierw skonfigurować połączenia pulpitu zdalnego. Wybierz pozycję **włącz pulpit zdalny** dla wszystkich ról, a następnie podaj poświadczenia, które są używane do zdalnego nawiązywania połączenia w wyświetlonym oknie **Konfiguracja pulpit zdalny** . Zobacz [włączanie Podłączanie pulpitu zdalnego dla roli na platformie Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Aby włączyć Web Deploy dla wszystkich ról sieci Web w aplikacji, wybierz opcję **włącz Web Deploy dla wszystkich ról sieci Web**.

    Zostanie wyświetlony żółty trójkąt ostrzegawczy. Web Deploy domyślnie używa niezaufanego certyfikatu z podpisem własnym, co nie jest zalecane do przekazywania poufnych danych. Aby zabezpieczyć ten proces w przypadku danych poufnych, można dodać certyfikat SSL, który będzie używany na potrzeby połączeń Web Deploy. Ten certyfikat musi być zaufanym certyfikatem. Aby uzyskać więcej informacji, zobacz [udostępnianie narzędzia Web Deploy Secure](#make-web-deploy-secure).

1. Wybierz pozycję **dalej** , aby wyświetlić ekran **Podsumowanie** , a następnie wybierz pozycję **Publikuj** , aby wdrożyć usługę w chmurze.

    Usługa w chmurze jest publikowana. Utworzona maszyna wirtualna ma włączone połączenia zdalne dla usług IIS, dzięki czemu Web Deploy może służyć do aktualizowania ról sieci Web bez konieczności ich ponownego publikowania.

   > [!NOTE]
   > Jeśli masz więcej niż jedno wystąpienie skonfigurowane dla roli sieci Web, zostanie wyświetlony komunikat ostrzegawczy z informacją o tym, że każda rola sieci Web jest ograniczona do jednego wystąpienia tylko w pakiecie utworzonym w celu opublikowania aplikacji. Kliknij przycisk **OK**, aby kontynuować. Zgodnie z opisem w sekcji wymagania można mieć więcej niż jedną rolę sieci Web, ale tylko jedno wystąpienie każdej roli.

### <a name="update-your-web-role-by-using-web-deploy"></a>Aktualizowanie roli sieci Web przy użyciu Web Deploy

1. Aby użyć Web Deploy, wprowadź zmiany kodu w projekcie dla dowolnych ról sieci Web w programie Visual Studio, które chcesz opublikować, a następnie kliknij prawym przyciskiem myszy ten węzeł projektu w rozwiązaniu, a następnie wskaż polecenie **Publikuj**. Zostanie wyświetlone okno dialogowe **Publikowanie sieci Web** .

1. Obowiązkowe Jeśli został dodany zaufany certyfikat SSL do użycia dla połączeń zdalnych dla usług IIS, możesz wyczyścić pole wyboru **Zezwalaj na niezaufany certyfikat** . Aby uzyskać informacje dotyczące sposobu dodawania certyfikatu w celu zapewnienia Web Deploy zabezpieczenia, zapoznaj się z sekcją w **celu wprowadzenia Web Deploy zabezpieczeń** w dalszej części tego artykułu.

1. Aby można było używać Web Deploy, mechanizm publikowania wymaga nazwy użytkownika i hasła, które zostały skonfigurowane dla połączenia Pulpit zdalny podczas pierwszej publikacji pakietu.

   a. W polu **Nazwa użytkownika**wprowadź nazwę użytkownika.

   b. W polu **hasło**wprowadź hasło.

   c. Obowiązkowe Jeśli chcesz zapisać to hasło w tym profilu, wybierz pozycję **Zapisz hasło**.

1. Aby opublikować zmiany w roli sieci Web, wybierz pozycję **Publikuj**.

    W wierszu stanu zostanie wyświetlona wartość **Publikowanie rozpoczęta**. Po zakończeniu publikowania zostanie wyświetlony komunikat **Publikowanie zakończyło się pomyślnie** . Zmiany zostały teraz wdrożone w roli sieci Web na maszynie wirtualnej. Teraz możesz uruchomić aplikację platformy Azure w środowisku platformy Azure, aby przetestować zmiany.

### <a name="make-web-deploy-secure"></a>Zabezpieczanie narzędzia Web Deploy

1. Web Deploy domyślnie używa niezaufanego certyfikatu z podpisem własnym, co nie jest zalecane do przekazywania poufnych danych. Aby zabezpieczyć ten proces w przypadku danych poufnych, można dodać certyfikat SSL, który będzie używany na potrzeby połączeń Web Deploy. Ten certyfikat musi być zaufanym certyfikatem uzyskanym od urzędu certyfikacji (CA).

    Aby zapewnić Web Deploy zabezpieczenia dla każdej maszyny wirtualnej dla każdej z ról sieci Web, należy przekazać zaufany certyfikat, który ma być używany dla narzędzia Web Deploy do Azure Portal. Ten certyfikat gwarantuje, że certyfikat jest dodawany do maszyny wirtualnej, która jest tworzona dla roli sieci Web podczas publikowania aplikacji.

1. Aby dodać zaufany certyfikat SSL do usług IIS do użycia na potrzeby połączeń zdalnych, wykonaj następujące kroki:

   a. Aby nawiązać połączenie z maszyną wirtualną, na której działa rola sieci Web, wybierz wystąpienie roli sieci Web w programie **Cloud Explorer** lub **Eksplorator serwera**, a następnie wybierz polecenie **Połącz przy użyciu pulpit zdalny** . Aby uzyskać szczegółowe instrukcje dotyczące nawiązywania połączenia z maszyną wirtualną, zobacz [włączanie Podłączanie pulpitu zdalnego dla roli na platformie Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). W przeglądarce zostanie wyświetlony komunikat z prośbą o pobranie pliku `.rdp`.

   b. Aby dodać certyfikat SSL, Otwórz usługę zarządzania w Menedżerze usług IIS. W Menedżerze usług IIS Włącz protokół SSL, otwierając link **powiązania** w okienku **Akcja** . Zostanie wyświetlone okno dialogowe **Dodawanie powiązania witryny** . Wybierz pozycję **Dodaj**, a następnie na liście rozwijanej **Typ** wybierz pozycję https. Z listy **certyfikat SSL** wybierz certyfikat SSL, który został podpisany przez urząd certyfikacji i przekazany do Azure Portal. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień połączenia dla usługi zarządzania](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)).

      > [!NOTE]
      > W przypadku dodania zaufanego certyfikatu SSL żółty trójkąt ostrzegawczy nie pojawia się już w **Kreatorze publikacji**.

## <a name="include-files-in-the-service-package"></a>Uwzględnij pliki w pakiecie usługi

Może być konieczne uwzględnienie określonych plików w pakiecie usługi, aby były dostępne na maszynie wirtualnej utworzonej dla roli. Na przykład możesz chcieć dodać `.exe` lub plik `.msi`, który jest używany przez skrypt uruchamiania w pakiecie usługi. Może być też konieczne dodanie zestawu, który jest wymagany przez rolę sieci Web lub projekt roli proces roboczy. Aby dołączyć pliki, należy je dodać do rozwiązania dla aplikacji platformy Azure.

1. Aby dodać zestaw do pakietu usługi, wykonaj następujące czynności:

   a. W **Eksplorator rozwiązań**Otwórz węzeł projektu dla projektu, w którym brakuje zestawu, którego dotyczy odwołanie.
   b. Aby dodać zestaw do projektu, otwórz menu skrótów dla folderu **References** , a następnie wybierz **Dodaj odwołanie**. Zostanie wyświetlone okno dialogowe Dodawanie odwołania.
   c. Wybierz odwołanie, które chcesz dodać, a następnie wybierz przycisk **OK**. Odwołanie jest dodawane do listy w folderze **References** .
   d. Otwórz menu skrótów dla dodanego zestawu i wybierz polecenie **Właściwości**. Zostanie wyświetlone okno **Właściwości** .

      Aby dołączyć ten zestaw do pakietu usługi, na **liście Kopiuj lokalne** wybierz **wartość PRAWDA**.
1. W **Eksplorator rozwiązań** Otwórz węzeł projektu dla projektu, w którym brakuje zestawu, którego dotyczy odwołanie.

1. Aby dodać zestaw do projektu, otwórz menu skrótów dla folderu **References** , a następnie wybierz **Dodaj odwołanie**. Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

1. Wybierz odwołanie, które chcesz dodać, a następnie wybierz przycisk **OK** .

    Odwołanie jest dodawane do listy w folderze **References** .

1. Otwórz menu skrótów dla dodanego zestawu i wybierz polecenie **Właściwości**. Zostanie wyświetlona okno Właściwości.

1. Aby dołączyć ten zestaw do pakietu usługi, na liście **Kopiuj lokalne** wybierz pozycję **prawda**.

1. Aby uwzględnić pliki w pakiecie usługi, które zostały dodane do projektu roli sieci Web, otwórz menu skrótów dla tego pliku, a następnie wybierz polecenie **Właściwości**. W oknie **Właściwości** wybierz pozycję **zawartość** w polu listy **Akcja kompilacji** .

1. Aby uwzględnić pliki w pakiecie usługi, które zostały dodane do projektu roli procesu roboczego, otwórz menu skrótów dla tego pliku, a następnie wybierz polecenie **Właściwości**. W oknie **Właściwości** w polu listy **Kopiuj do katalogu wyjściowego** wybierz opcję **Kopiuj** .

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o publikowaniu na platformie Azure z programu Visual Studio, zobacz [Kreator publikowania aplikacji platformy Azure](vs-azure-tools-publish-azure-application-wizard.md).
