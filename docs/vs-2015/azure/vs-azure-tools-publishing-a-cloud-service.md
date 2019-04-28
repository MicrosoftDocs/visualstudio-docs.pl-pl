---
title: Publikowanie usługi w chmurze przy użyciu narzędzi platformy Azure | Dokumentacja firmy Microsoft
description: Dowiedz się więcej o sposobie publikowania projektów usług w chmurze platformy Azure przy użyciu programu Visual Studio.
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
ms.openlocfilehash: c13d2e2a8f0ec06cdec26763e3492bfce7acfad0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830550"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publikowanie usługi w chmurze za pomocą programu Visual Studio

Program Visual Studio można opublikować aplikacji bezpośrednio na platformie Azure dzięki obsłudze środowisk przemieszczania i produkcji, usługi w chmurze. Podczas publikowania, możesz wybrać środowisko wdrażania i konto magazynu jest używane tymczasowo pakietu wdrożeniowego.

Opublikuj zmiany przyrostowe dla swoich ról sieci web w podczas tworzenia i testowania aplikacji systemu Azure, można użyć narzędzia Web Deploy. Po opublikowaniu aplikacji w środowisku wdrażania narzędzia Web Deploy umożliwia wdrażanie zmian bezpośrednio do maszyny wirtualnej, na którym działa rola sieci web. Nie trzeba w pakietach i publikowanie aplikacji platformy Azure cały każdorazowo, które chcesz zaktualizować roli sieci web, aby przetestować zmiany. To podejście może mieć dostępne zmiany roli sieci web w chmurze, testowanie bez oczekiwania na zostały opublikowane w środowisku wdrażania aplikacji.

Publikowanie aplikacji platformy Azure i zaktualizuj rolę sieci web za pomocą narzędzia Web Deploy, należy użyć poniższych procedur:

- Publikowanie lub pakietu aplikacji systemu Azure z programu Visual Studio
- Zaktualizuj rolę sieci web w ramach tworzenia i testowania cyklu

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publikowanie lub pakietu aplikacji systemu Azure z programu Visual Studio

Podczas publikowania aplikacji systemu Azure, możesz wykonać jedną z następujących czynności:

- Utwórz pakiet usługi: Można użyć tego pakietu i pliku konfiguracji usługi, aby opublikować aplikację w środowisku wdrażania z [witryny Azure portal](https://portal.azure.com).

- Publikowanie projektu platformy Azure z programu Visual Studio: Aby opublikować aplikację bezpośrednio na platformie Azure, należy użyć Kreatora publikacji. Aby uzyskać informacje, zobacz [Kreator publikowania aplikacji Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Aby utworzyć pakiet usługi w programie Visual Studio

1. Gdy jesteś gotowy opublikować aplikację, otwórz Solution Explorer, otwórz menu skrótów dla projektu platformy Azure, który zawiera role i wybierz polecenie Publikuj.

1. Aby utworzyć pakietu usług, wykonaj następujące kroki:

   a. W menu skrótów dla projektu platformy Azure wybierz **pakietu**.

   b. W **pakietu aplikacji na platformie Azure** okno dialogowe, wybierz konfigurację usługi, dla której chcesz utworzyć pakiet, a następnie wybierz konfigurację kompilacji.

   c. (Opcjonalnie) Aby włączyć Pulpit zdalny dla usługi w chmurze po opublikowaniu, wybierz pozycję **Włącz pulpit zdalny dla wszystkich ról**, a następnie wybierz pozycję **ustawienia** konfigurowania poświadczeń pulpitu zdalnego. Aby uzyskać więcej informacji, zobacz [Włącz Podłączanie pulpitu zdalnego dla roli w usługach Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Jeśli chcesz debugować usługi w chmurze, po opublikowaniu, włączyć zdalne debugowanie, wybierając **Włączanie zdalnego debugera dla wszystkich ról**.

   d. Aby utworzyć pakiet, wybierz opcję **pakietu** łącza.

      Eksplorator plików zawiera lokalizację pliku nowo utworzonego pakietu. Możesz skopiować tę lokalizację, aby można go używać w witrynie Azure portal.

   e. Aby opublikować środowisko wdrażania tego pakietu, należy użyć tej lokalizacji jako lokalizacja pakietu podczas tworzenia usługi w chmurze i wdrażania tego pakietu do środowiska w witrynie Azure portal.

1. (Opcjonalnie) Aby anulować procesu wdrażania w menu skrótów dla pozycji w dzienniku aktywności, wybierz **Anuluj i Usuń**. To polecenie powoduje zatrzymanie procesu wdrażania i usuwa środowisko wdrażania na platformie Azure. Aby usunąć środowiska po wdrożeniu, należy użyć witryny Azure portal.

1. (Opcjonalnie) Po rozpoczęciu mają wystąpień roli, Visual Studio automatycznie wyświetla środowisko wdrażania w **usług w chmurze** węzła w Eksploratorze serwera. W tym miejscu można wyświetlić stan poszczególne wystąpienia ról. Zobacz [Zarządzanie zasobów platformy Azure za pomocą Eksploratora chmury](vs-azure-tools-resources-managing-with-cloud-explorer.md). Na poniższej ilustracji przedstawiono wystąpień roli, gdy są one nadal w stanie inicjowanie:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Zaktualizuj rolę sieci web w ramach tworzenia i testowania cyklu

Zaktualizuj rolę sieci web w projekcie w przypadku infrastruktury zaplecza aplikacji jest stabilna, ale ról sieć web bardziej wymagają częstego aktualizowania, można użyć narzędzia Web Deploy. Narzędzie Web Deploy jest przydatne, gdy nie chcesz ponownie skompiluj i wdróż role procesu roboczego zaplecza lub jeśli masz wiele ról sieć web i chcesz zaktualizować tylko jedną z ról sieci web.

### <a name="requirements-for-using-web-deploy"></a>Wymagania dotyczące korzystania z narzędzia Web Deploy

- **Do tworzenia i testowania wyłącznie do celów**: Zmiany zostaną wprowadzone bezpośrednio do maszyny wirtualnej, w którym jest uruchomiona rola sieci web. Jeśli ta maszyna wirtualna ma zostać odzyskany, zmiany zostaną utracone, ponieważ oryginalny pakiet, który został opublikowany jest używana do odtworzenia maszyny wirtualnej dla roli. Ponownie opublikować aplikację, aby pobrać najnowsze zmiany w roli sieci web.

- **Można aktualizować tylko role sieci web**: Nie można zaktualizować ról procesów roboczych. Ponadto nie można zaktualizować `RoleEntryPoint` w `web role.cs`.

- **Może obsługiwać tylko jedno wystąpienie roli sieci web**: Nie może mieć wiele wystąpień dowolnej roli sieci web w środowisku wdrażania. Wiele ról sieci web każdy tylko z jednym wystąpieniem są jednak obsługiwane.

- **Włączenie połączeń pulpitu zdalnego**: Wymaganie to umożliwia, narzędzie Web Deploy na potrzeby połączenia z maszyną wirtualną, aby wdrożyć zmiany dla serwera, na którym działa program Internet Information Services (IIS) użytkownika i hasło. Ponadto może być konieczne łączenie z maszyną wirtualną, aby dodać zaufany certyfikat usług IIS na tej maszynie wirtualnej. (Ten certyfikat zapewnia to bezpieczne połączenia zdalnego dla usług IIS, która jest używana przez narzędzia Web Deploy).

W poniższej procedurze przyjęto, że używasz **publikowanie aplikacji platformy Azure** kreatora.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Włącz narzędzia Web Deploy, gdy opublikujesz aplikację

1. Aby włączyć **Włącz narzędzia Web Deploy dla wszystkich ról sieci web** opcji, należy najpierw skonfigurować połączenia pulpitu zdalnego. Wybierz **Włącz pulpit zdalny** dla wszystkich ról, a następnie podaj poświadczenia, które służy do łączenia zdalnie w **konfiguracji pulpitu zdalnego** zostanie wyświetlone okno. Zobacz [Włącz Podłączanie pulpitu zdalnego dla roli w usługach Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Aby włączyć narzędzia Web Deploy dla wszystkich ról sieci web w aplikacji, wybierz **Włącz narzędzia Web Deploy dla wszystkich ról sieci web**.

    Żółty trójkąt ostrzeżenie zostanie wyświetlone. Narzędzie Web Deploy używa niezaufanego certyfikatu podpisem domyślnie, co nie jest zalecany do przekazywania poufnych danych. Jeśli potrzebujesz zabezpieczyć ten proces dla danych poufnych, można dodać certyfikatu SSL do użytku z połączenia narzędzia Web Deploy. Ten certyfikat musi być zaufany certyfikat. Aby uzyskać więcej informacji, zobacz [zabezpieczyć sieci web wdrażanie](#make-web-deploy-secure).

1. Wybierz **dalej** pokazanie **Podsumowanie** ekranu, a następnie wybierz **Publikuj** wdrożyć usługę w chmurze.

    Usługi w chmurze została opublikowana. Maszyny wirtualnej, która jest tworzona ma włączone dla usług IIS tak, aby narzędzie Web Deploy można zaktualizować Twoje role internetowe bez konieczności ponownego publikowania ich połączeń zdalnych.

   > [!NOTE]
   > Jeśli masz więcej niż jedno wystąpienie skonfigurowany dla roli sieci web, pojawi się komunikat ostrzegawczy z informacją, że każda rola sieci web jest ograniczona do jednego wystąpienia tylko w pakiecie, który jest tworzony, aby opublikować aplikację. Wybierz **OK** aby kontynuować. Jak wspomniano w sekcji wymagania, możesz mieć więcej niż jednej roli sieci web, ale tylko jedno wystąpienie każdej roli.

### <a name="update-your-web-role-by-using-web-deploy"></a>Aktualizowanie roli sieci web za pomocą narzędzia Web Deploy

1. Aby korzystać z narzędzia Web Deploy, zmiany kodu do projektu dla każdej z ról sieci web w programie Visual Studio, który chcesz opublikować, a następnie kliknij prawym przyciskiem myszy ten węzeł projektu w rozwiązaniu i wskaż **Publikuj**. **Publikowanie w sieci Web** pojawi się okno dialogowe.

1. (Opcjonalnie) Jeśli został dodany zaufany certyfikat SSL na potrzeby połączeń zdalnych w usługach IIS, można wyczyścić **Zezwalaj niezaufany certyfikat** pole wyboru. Aby uzyskać informacje o tym, jak dodać certyfikat, aby zwiększyć bezpieczeństwo narzędzia Web Deploy, zobacz sekcję **do upewnij sieci Web wdrażanie bezpiecznych** w dalszej części tego artykułu.

1. Aby korzystać z narzędzia Web Deploy, mechanizmu publikowania wymaga nazwy użytkownika i hasło, które można skonfigurować połączenia pulpitu zdalnego podczas pierwszej publikacji pakietu.

   a. W **nazwa_użytkownika**, wprowadź nazwę użytkownika.

   b. W **hasło**, wprowadź hasło.

   c. (Opcjonalnie) Jeśli chcesz zapisać to hasło w tym profilu, wybierz opcję **Zapisz hasło**.

1. Aby opublikować zmiany w roli sieci web, wybierz **Publikuj**.

    Wyświetla wiersz stanu **Publikuj pracę**. Po zakończeniu publikowania **Publikowanie powiodło się** pojawia się. Zmiany zostały wdrożone obecnie do roli sieci web na maszynie wirtualnej. Teraz można uruchomić aplikacji platformy Azure w środowisku platformy Azure, aby przetestować zmiany.

### <a name="make-web-deploy-secure"></a>Zwiększanie bezpieczeństwa wdrożenia w sieci web

1. Narzędzie Web Deploy używa niezaufanego certyfikatu podpisem domyślnie, co nie jest zalecany do przekazywania poufnych danych. Jeśli potrzebujesz zabezpieczyć ten proces dla danych poufnych, można dodać certyfikatu SSL do użytku z połączenia narzędzia Web Deploy. Ten certyfikat musi być zaufany certyfikat, który można uzyskać od urzędu certyfikacji (CA).

    Aby zabezpieczyć narzędzia Web Deploy dla każdej maszyny wirtualnej dla każdej z ról sieci web, należy przekazać zaufanego certyfikatu, którego chcesz używać dla sieci web wdrożenia do witryny Azure portal. Ten certyfikat gwarantuje, że certyfikat został dodany do maszyny wirtualnej, która jest tworzona dla roli sieci web, gdy opublikujesz aplikację.

1. Aby dodać zaufany certyfikat SSL w usługach IIS na potrzeby połączeń zdalnych, wykonaj następujące kroki:

   a. Aby połączyć z maszyną wirtualną, która jest uruchomiona rola sieci web, wybierz wystąpienie roli sieci web w **Eksploratora chmury** lub **Eksploratora serwera**, a następnie wybierz **nawiązywanie połączenia przy użyciu pulpitu zdalnego**  polecenia. Aby uzyskać szczegółowe instrukcje na temat nawiązywania połączenia z maszyną wirtualną, zobacz [Włącz Podłączanie pulpitu zdalnego dla roli w usługach Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Przeglądarka wyświetli monit o Pobierz `.rdp` pliku.

   b. Aby dodać certyfikat protokołu SSL, otwórz usługę zarządzania w Menedżerze usług IIS. W Menedżerze usług IIS, Włącz protokół SSL, otwierając **powiązania** łącze w **akcji** okienka. **Dodawanie powiązania witryny** pojawi się okno dialogowe. Wybierz **Dodaj**, a następnie wybierz pozycję HTTPS **typu** listy rozwijanej. W **certyfikat SSL** wybierz certyfikat SSL, użytkownik miał zarejestrowany przez urząd certyfikacji i przekazany do witryny Azure portal. Aby uzyskać więcej informacji, zobacz [skonfigurować ustawienia połączenia z usługą zarządzania](http://go.microsoft.com/fwlink/?LinkId=215824).

      > [!NOTE]
      > Jeśli dodasz zaufany certyfikat SSL, żółty trójkąt ostrzeżenie nie jest już wyświetlany w **Kreatora publikacji**.

## <a name="include-files-in-the-service-package"></a>Dołącz pliki w pakiecie usługi

Może być konieczne obejmują określonych plików w pakiecie usługi, tak aby były dostępne na maszynie wirtualnej, który jest tworzony dla roli. Na przykład możesz chcieć dodać `.exe` lub `.msi` pliku, który jest używany przez skrypt uruchamiania pakietu usługi. Lub może być konieczne dodanie zestawu, który wymaga projektu roli sieć web, jak rola lub proces roboczy. Podczas dołączania plików, należy dodać do rozwiązania dla aplikacji systemu Azure.

1. Aby dodać zestaw do pakietu usług, użyj następujących kroków:

   a. W **Eksploratora rozwiązań**, otwórz węzeł projektu dla projektu, który jest brak przywoływanego zestawu.
   b. Aby dodać zestaw do projektu, otwórz menu skrótów dla **odwołania** folder, a następnie wybierz **Dodaj odwołanie**. Pojawi się okno dialogowe Dodaj odwołanie.
   c. Wybierz odwołanie, które chcesz dodać, a następnie wybierz **OK**. Odwołania są dodawane do listy w obszarze **odwołania** folderu.
   d. Otwórz menu skrótów dla zestawu, który został dodany, a następnie wybierz **właściwości**. **Właściwości** zostanie wyświetlone okno.

      Aby dołączyć ten zestaw w pakiecie usługi **kopię lokalną listę** wybierz **True**.
1. W **Eksploratora rozwiązań** Otwórz węzeł projektu dla projektu, który jest brak przywoływanego zestawu.

1. Aby dodać zestaw do projektu, otwórz menu skrótów dla **odwołania** folder, a następnie wybierz **Dodaj odwołanie**. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

1. Wybierz odwołanie, które chcesz dodać, a następnie wybierz **OK** przycisku.

    Odwołania są dodawane do listy w obszarze **odwołania** folderu.

1. Otwórz menu skrótów dla zestawu, który został dodany, a następnie wybierz **właściwości**. Zostanie wyświetlone okno właściwości.

1. Aby uwzględnić ten zestaw w pakiecie usługi w **Kopiuj lokalnie** wybierz **True**.

1. Aby dołączyć pliki w pakiecie usługi, które zostały dodane do projektu roli sieci web, otwórz menu skrótów dla pliku, a następnie wybierz **właściwości**. Z **właściwości** oknie Wybierz **zawartości** z **Build Action** pola listy.

1. Aby dołączyć pliki w pakiecie usługi, które zostały dodane do projektu roli proces roboczy, otwórz menu skrótów dla pliku, a następnie wybierz **właściwości**. Z **właściwości** oknie Wybierz **Kopiuj Jeśli nowszy** z **Kopiuj do katalogu wyjściowego** pola listy.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o funkcji publikowania na platformie Azure z programu Visual Studio, zobacz [Kreator publikowania aplikacji Azure](vs-azure-tools-publish-azure-application-wizard.md).
