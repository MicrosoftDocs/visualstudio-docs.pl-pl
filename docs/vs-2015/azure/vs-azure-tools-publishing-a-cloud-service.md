---
title: Publikowanie usługi w chmurze przy użyciu narzędzi platformy Azure | Dokumenty firmy Microsoft
description: Dowiedz się, jak publikować projekty usługi w chmurze platformy Azure przy użyciu programu Visual Studio.
author: ghogen
manager: jillfra
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: b959d411f0f574b03729d8016feb6efc531ae171
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302561"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publikowanie usługi w chmurze za pomocą programu Visual Studio

Visual Studio można opublikować aplikację bezpośrednio na platformie Azure, z obsługą środowisk przejściowych i produkcyjnych usługi w chmurze. Podczas publikowania należy wybrać środowisko wdrażania i konto magazynu, które jest tymczasowo używane dla pakietu wdrożeniowego.

Podczas tworzenia i testowania aplikacji platformy Azure, można użyć wdrażania sieci Web, aby publikować zmiany przyrostowo dla ról sieci web. Po opublikowaniu aplikacji w środowisku wdrażania, Web Deploy umożliwia wdrażanie zmian bezpośrednio na maszynie wirtualnej, która jest uruchomiona roli sieci web. Nie trzeba pakować i publikować całej aplikacji platformy Azure za każdym razem, gdy chcesz zaktualizować rolę sieci web, aby przetestować zmiany. Dzięki takiemu podejściu można mieć zmiany roli sieci web dostępne w chmurze do testowania bez oczekiwania na opublikowanie aplikacji w środowisku wdrażania.

Skorzystaj z następujących procedur, aby opublikować aplikację platformy Azure i zaktualizować rolę sieci Web przy użyciu narzędzia Web Deploy:

- Publikowanie lub pakowanie aplikacji platformy Azure z programu Visual Studio
- Aktualizowanie roli sieci Web w ramach cyklu tworzenia i testowania

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publikowanie lub pakowanie aplikacji platformy Azure z programu Visual Studio

Podczas publikowania aplikacji platformy Azure można wykonać jedno z następujących zadań:

- Utwórz pakiet usługi: Można użyć tego pakietu i pliku konfiguracji usługi, aby opublikować aplikację w środowisku wdrażania z [witryny Azure portal](https://portal.azure.com).

- Opublikuj swój projekt platformy Azure z programu Visual Studio: Aby opublikować aplikację bezpośrednio na platformie Azure, użyj Kreatora publikowania. Aby uzyskać więcej informacji, zobacz [Kreator publikowania aplikacji platformy Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Aby utworzyć pakiet usługi z programu Visual Studio

1. Gdy będziesz gotowy do opublikowania aplikacji, otwórz Eksploratora rozwiązań, otwórz menu skrótów dla projektu platformy Azure, który zawiera twoje role, i wybierz pozycję Publikuj.

1. Aby utworzyć tylko pakiet usług, wykonaj następujące kroki:

   a. W menu skrótów dla projektu platformy Azure wybierz pozycję **Pakiet**.

   b. W oknie dialogowym **Pakiet aplikacji platformy Azure** wybierz konfigurację usługi, dla której chcesz utworzyć pakiet, a następnie wybierz konfigurację kompilacji.

   d. (Opcjonalnie) Aby włączyć pulpit zdalny usługi w chmurze po jej opublikowaniu, wybierz pozycję **Włącz pulpit zdalny dla wszystkich ról**, a następnie wybierz pozycję **Ustawienia,** aby skonfigurować poświadczenia pulpitu zdalnego. Aby uzyskać więcej informacji, zobacz [Włączanie połączenia pulpitu zdalnego dla roli w usługach w chmurze azure przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Jeśli chcesz debugować usługę w chmurze po jej opublikowaniu, włącz zdalne debugowanie, wybierając **pozycję Włącz debuger zdalny dla wszystkich ról**.

   d. Aby utworzyć pakiet, wybierz łącze **Pakiet.**

      Eksplorator plików pokazuje lokalizację pliku nowo utworzonego pakietu. Tę lokalizację można skopiować, aby można było jej używać z witryny Azure Portal.

   e. Aby opublikować ten pakiet w środowisku wdrażania, należy użyć tej lokalizacji jako lokalizacji pakietu podczas tworzenia usługi w chmurze i wdrażania tego pakietu w środowisku za pomocą witryny Azure portal.

1. (Opcjonalnie) Aby anulować proces wdrażania, w menu skrótów elementu zamówienia w dzienniku aktywności wybierz pozycję **Anuluj i usuń**. To polecenie zatrzymuje proces wdrażania i usuwa środowisko wdrażania z platformy Azure. Aby usunąć środowisko po wdrożeniu, użyj witryny Azure portal.

1. (Opcjonalnie) Po uruchomieniu wystąpień roli program Visual Studio automatycznie wyświetla środowisko wdrażania w węźle Usługi w **chmurze** w Eksploratorze serwera. W tym miejscu można zobaczyć stan poszczególnych wystąpień roli. Zobacz [Zarządzanie zasobami platformy Azure za pomocą Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md). Na poniższej ilustracji przedstawiono wystąpienia roli, gdy są one nadal w stanie inicjowania:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Aktualizowanie roli sieci Web w ramach cyklu tworzenia i testowania

Jeśli infrastruktura zaplecza aplikacji jest stabilna, ale role sieci web wymagają częstszego aktualizowania, można użyć wdrożenia w sieci Web, aby zaktualizować tylko rolę sieci Web w projekcie. Wdrażanie w sieci Web jest przydatne, gdy nie chcesz odbudować i ponownie wdrożyć ról roboczego zaplecza lub jeśli masz wiele ról sieci Web i chcesz zaktualizować tylko jedną z ról sieci Web.

### <a name="requirements-for-using-web-deploy"></a>Wymagania dotyczące korzystania z wdrażania w sieci Web

- **Tylko do celów deweloperskich i testowych:** zmiany są wprowadzane bezpośrednio do maszyny wirtualnej, na której jest uruchomiona rola sieci web. Jeśli ta maszyna wirtualna ma zostać odtworzona, zmiany zostaną utracone, ponieważ oryginalny pakiet, który został opublikowany jest używany do ponownego tworzenia maszyny wirtualnej dla roli. Ponownie opublikuj aplikację, aby uzyskać najnowsze zmiany dla roli sieci web.

- **Można aktualizować tylko role sieci Web:** nie można aktualizować ról procesu roboczego. Ponadto nie można zaktualizować w `RoleEntryPoint` `web role.cs`.

- **Może obsługiwać tylko jedno wystąpienie roli sieci web:** nie można mieć wielu wystąpień dowolnej roli sieci web w środowisku wdrażania. Jednak wiele ról sieci web, z których każda ma tylko jedno wystąpienie, jest obsługiwanych.

- **Włącz połączenia pulpitu zdalnego:** To wymaganie umożliwia wdrażaniu w sieci Web za pomocą użytkownika i hasła do łączenia się z maszyną wirtualną w celu wdrożenia zmian na serwerze z uruchomionymi usługami internet information services (IIS). Ponadto może być konieczne połączenie z maszyną wirtualną, aby dodać zaufany certyfikat do usług IIS na tej maszynie wirtualnej. (Ten certyfikat gwarantuje, że połączenie zdalne dla usług IIS używane przez program Web Deploy jest bezpieczne).

W poniższej procedurze przyjęto założenie, że używasz kreatora **publikowania aplikacji platformy Azure.**

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Włączanie wdrażania w sieci Web podczas publikowania aplikacji

1. Aby włączyć opcję **Włącz wdrażanie sieci Web dla wszystkich ról sieci Web,** należy najpierw skonfigurować połączenia pulpitu zdalnego. Wybierz **pozycję Włącz pulpit zdalny** dla wszystkich ról, a następnie podaj poświadczenia używane do zdalnego łączenia się w wyświetlonym polu **Konfiguracja pulpitu zdalnego.** Zobacz [Włączanie połączenia pulpitu zdalnego dla roli w usługach w chmurze platformy Azure przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Aby włączyć wdrażanie w sieci Web dla wszystkich ról sieci Web w aplikacji, wybierz pozycję **Włącz wdrażanie w sieci Web dla wszystkich ról sieci Web**.

    Pojawi się żółty trójkąt ostrzegawczy. Program Web Deploy domyślnie używa niezaufanego certyfikatu z podpisem własnym, który nie jest zalecany do przekazywania poufnych danych. Jeśli chcesz zabezpieczyć ten proces dla poufnych danych, możesz dodać certyfikat SSL, który ma być używany do wdrażania w sieci Web połączeń. Ten certyfikat musi być zaufanym certyfikatem. Aby uzyskać więcej informacji, zobacz [Bezpieczne wdrażanie sieci Web](#make-web-deploy-secure).

1. Wybierz **pozycję Dalej,** aby wyświetlić ekran **Podsumowanie,** a następnie wybierz pozycję **Publikuj,** aby wdrożyć usługę w chmurze.

    Usługa w chmurze jest publikowana. Utworzona maszyna wirtualna ma włączone połączenia zdalne dla usług IIS, dzięki czemu wdrażanie w sieci Web może służyć do aktualizowania ról sieci Web bez ich ponownego publikowania.

   > [!NOTE]
   > Jeśli dla roli sieci web skonfigurowano więcej niż jedno wystąpienie, zostanie wyświetlony komunikat ostrzegawczy informujący, że każda rola sieci web jest ograniczona do jednego wystąpienia tylko w pakiecie utworzonym w celu opublikowania aplikacji. Kliknij przycisk **OK**, aby kontynuować. Jak podano w sekcji Wymagania, można mieć więcej niż jedną rolę sieci web, ale tylko jedno wystąpienie każdej roli.

### <a name="update-your-web-role-by-using-web-deploy"></a>Aktualizowanie roli sieci Web przy użyciu wdrażania w sieci Web

1. Aby użyć programu Web Deploy, należy wprowadzić zmiany kodu w projekcie dla dowolnej roli sieci Web w programie Visual Studio, które chcesz opublikować, a następnie kliknij prawym przyciskiem myszy ten węzeł projektu w rozwiązaniu i wskaż polecenie **Publikuj**. Zostanie wyświetlone okno dialogowe **Publikowanie w sieci Web.**

1. (Opcjonalnie) Jeśli dodano zaufany certyfikat SSL do użycia w połączeniach zdalnych dla usług IIS, można wyczyścić pole wyboru **Zezwalaj na niezaufany certyfikat.** Aby uzyskać informacje dotyczące dodawania certyfikatu w celu zabezpieczenia wdrożenia w sieci Web, zobacz sekcję **Aby wdrożenie sieci Web było bezpieczne** w dalszej części tego artykułu.

1. Aby użyć narzędzia Web Deploy, mechanizm publikowania wymaga nazwy użytkownika i hasła skonfigurowanych dla połączenia pulpitu zdalnego podczas pierwszego opublikowania pakietu.

   a. W **pliku User name**wprowadź nazwę użytkownika.

   b. W **obszarze Hasło**wprowadź hasło.

   d. (Opcjonalnie) Jeśli chcesz zapisać to hasło w tym profilu, wybierz pozycję **Zapisz hasło**.

1. Aby opublikować zmiany w roli sieci Web, wybierz pozycję **Publikuj**.

    W wierszu stanu jest wyświetlany komunikat **Publish started**. Po zakończeniu publikowania zostanie **wyświetlony program Publikowania.** Zmiany zostały wdrożone do roli sieci web na maszynie wirtualnej. Teraz możesz uruchomić aplikację platformy Azure w środowisku platformy Azure, aby przetestować zmiany.

### <a name="make-web-deploy-secure"></a>Bezpieczne wdrażanie w sieci Web

1. Program Web Deploy domyślnie używa niezaufanego certyfikatu z podpisem własnym, który nie jest zalecany do przekazywania poufnych danych. Jeśli chcesz zabezpieczyć ten proces dla poufnych danych, możesz dodać certyfikat SSL, który ma być używany do wdrażania w sieci Web połączeń. Ten certyfikat musi być zaufanym certyfikatem, który można uzyskać od urzędu certyfikacji.This certificate needs to be a trusted certificate, which you obtain from a certificate authority (CA).

    Aby program Web Deploy był bezpieczny dla każdej maszyny wirtualnej dla każdej z ról sieci Web, należy przekazać zaufany certyfikat, którego chcesz użyć do wdrożenia w sieci Web w witrynie Azure portal. Ten certyfikat zapewnia, że certyfikat jest dodawany do maszyny wirtualnej, która jest tworzona dla roli sieci web podczas publikowania aplikacji.

1. Aby dodać zaufany certyfikat SSL do usług IIS do użycia w przypadku połączeń zdalnych, wykonaj następujące kroki:

   a. Aby połączyć się z maszyną wirtualną, na którą działa rola sieci Web, wybierz wystąpienie roli sieci Web w **Eksploratorze chmury** lub **Eksploratorze serwera,** a następnie wybierz polecenie **Połącz za pomocą pulpitu zdalnego.** Aby uzyskać szczegółowe instrukcje dotyczące łączenia się z maszyną wirtualną, zobacz [Włączanie połączenia pulpitu zdalnego dla roli w usługach w chmurze platformy Azure przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Przeglądarka wyświetli monit o `.rdp` pobranie pliku.

   b. Aby dodać certyfikat SSL, otwórz usługę zarządzania w Menedżerze usług IIS. W Menedżerze usług IIS włącz SSL, otwierając łącze **Powiązania** w okienku **Akcja.** Zostanie wyświetlone okno dialogowe **Dodawanie powiązania witryny.** Wybierz **pozycję Dodaj**, a następnie wybierz pozycję HTTPS na liście rozwijanej **Typ.** Na liście **certyfikatów SSL** wybierz certyfikat SSL podpisany przez urząd certyfikacji i przekazany do witryny Azure portal. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień połączenia dla usługi zarządzania](https://technet.microsoft.com/library/cc770458(WS.10).aspx).

      > [!NOTE]
      > Po dodaniu zaufanego certyfikatu SSL żółty trójkąt ostrzegawczy nie będzie już wyświetlany w **Kreatorze publikowania**.

## <a name="include-files-in-the-service-package"></a>Dołączanie plików do pakietu usług

Może być konieczne dołączenie określonych plików w pakiecie usługi, tak aby były one dostępne na maszynie wirtualnej, która jest tworzona dla roli. Na przykład można dodać `.exe` lub `.msi` plik, który jest używany przez skrypt startowy do pakietu usługi. Lub może być konieczne dodanie zestawu, który wymaga roli sieci web lub projektu roli procesu roboczego. Aby dołączyć pliki, należy je dodać do rozwiązania dla aplikacji platformy Azure.

1. Aby dodać zestaw do pakietu serwisowego, należy wykonać następujące czynności:

   a. W **Eksploratorze rozwiązań**otwórz węzeł projektu dla projektu, dla którego brakuje zestawu, do którego istnieje odwołanie.
   b. Aby dodać zestaw do projektu, otwórz menu skrótów dla folderu **Odwołania,** a następnie wybierz pozycję **Dodaj odwołanie**. Zostanie wyświetlone okno dialogowe Dodaj odwołanie.
   d. Wybierz odwołanie, które chcesz dodać, a następnie wybierz przycisk **OK**. Odwołanie zostanie dodane do listy w folderze **Odwołania.**
   d. Otwórz menu skrótów dla dodanego złożenia i wybierz polecenie **Właściwości**. Zostanie wyświetlone okno **Właściwości.**

      Aby uwzględnić ten zestaw w pakiecie usług, na **liście Kopiuj lokalnie** wybierz pozycję **True**.
1. W **Eksploratorze rozwiązań** otwórz węzeł projektu dla projektu, w którego brakuje zestawu, do którego istnieje odwołanie.

1. Aby dodać zestaw do projektu, otwórz menu skrótów dla folderu **Odwołania,** a następnie wybierz pozycję **Dodaj odwołanie**. Zostanie wyświetlone okno dialogowe **Dodaj odwołanie.**

1. Wybierz odwołanie, które chcesz dodać, a następnie wybierz przycisk **OK.**

    Odwołanie zostanie dodane do listy w folderze **Odwołania.**

1. Otwórz menu skrótów dla dodanego złożenia i wybierz polecenie **Właściwości**. Zostanie wyświetlone okno Właściwości.

1. Aby uwzględnić ten zestaw w pakiecie usług, na liście **Kopiuj lokalnie** wybierz pozycję **True**.

1. Aby uwzględnić pliki w pakiecie usług, które zostały dodane do projektu roli sieci Web, otwórz menu **skrótów**dla pliku, a następnie wybierz polecenie Właściwości . W oknie **Właściwości** wybierz pozycję **Zawartość** z pola listy **Akcja kompilacji.**

1. Aby uwzględnić pliki w pakiecie usług, które zostały dodane do projektu roli procesu roboczego, otwórz menu **skrótów**dla pliku, a następnie wybierz polecenie Właściwości . W oknie **Właściwości** wybierz polecenie **Kopiuj, jeśli jest nowsza** z pola listy **Kopiuj do katalogu wyjściowego.**

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o publikowaniu na platformie Azure w programie Visual Studio, zobacz [Kreator publikowania aplikacji platformy Azure](vs-azure-tools-publish-azure-application-wizard.md).
