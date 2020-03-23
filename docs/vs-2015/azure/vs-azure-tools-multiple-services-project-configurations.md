---
title: Konfigurowanie projektu platformy Azure przy użyciu wielu konfiguracji usług | Dokumenty firmy Microsoft
description: Dowiedz się, jak skonfigurować projekt usługi w chmurze platformy Azure, zmieniając pliki ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg i ServiceConfiguration.Cloud.cscfg.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 59996180661806eee60d18ab4b7b5fd26f4a2e7b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302575"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Konfigurowanie projektu platformy Azure w programie Visual Studio w celu używania wielu konfiguracji usługi

Projekt usługi w chmurze platformy Azure `ServiceDefinition.csdef`w `ServiceConfiguration.Local.cscfg`programie `ServiceConfiguration.Cloud.cscfg`Visual Studio zawiera trzy pliki konfiguracyjne: , i :

- `ServiceDefinition.csdef`jest wdrażany na platformie Azure, aby opisać wymagania usługi w chmurze i jej ról oraz aby zapewnić ustawienia, które mają zastosowanie do wszystkich wystąpień. Ustawienia można odczytać w czasie wykonywania przy użyciu interfejsu API środowiska wykonawczego hostingu usługi azure. Ten plik można zaktualizować na platformie Azure tylko wtedy, gdy usługa w chmurze jest zatrzymana.
- `ServiceConfiguration.Local.cscfg`i `ServiceConfiguration.Cloud.cscfg` podaj wartości ustawień w pliku definicji i określ liczbę wystąpień do uruchomienia dla każdej roli. Plik "Lokalny" zawiera wartości używane w debugowaniu lokalnym; plik "Chmura" jest wdrażany `ServiceConfiguration.cscfg` na platformie Azure jako i udostępnia ustawienia dla środowiska serwera. Ten plik można zaktualizować, gdy usługa w chmurze jest uruchomiona na platformie Azure.

Ustawienia konfiguracji są zarządzane i modyfikowane w programie Visual Studio przy użyciu stron właściwości dla odpowiedniej roli (kliknij prawym przyciskiem myszy rolę i wybierz **polecenie Właściwości**lub kliknij dwukrotnie rolę). Zmiany mogą być ograniczone do dowolnej konfiguracji jest wybrany w **konfiguracji usługi** listy rozwijanej. Właściwości ról sieci web i procesu roboczego są podobne, z wyjątkiem przypadków opisanych w poniższych sekcjach.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Aby uzyskać informacje na temat podstawowych schematów dla plików konfiguracji definicji usługi i usługi, zobacz schemat [XML csdef](/azure/cloud-services/schema-csdef-file) i [.cscfg XML Schema](/azure/cloud-services/schema-cscfg-file) artykułów. Aby uzyskać więcej informacji na temat konfiguracji usługi, zobacz [Jak skonfigurować usługi w chmurze](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Strona konfiguracji

### <a name="service-configuration"></a>Konfiguracja usługi

Wybiera, `ServiceConfiguration.*.cscfg` na który plik mają wpływ zmiany. Domyślnie istnieją warianty lokalne i chmurowe i można użyć polecenia **Zarządzaj...** do kopiowania, zmieniania nazwy i usuwania plików konfiguracyjnych. Pliki te są dodawane do projektu usługi w chmurze i pojawiają się w **Eksploratorze rozwiązań**. Jednak zmiana nazwy lub usunięcie konfiguracji można wykonać tylko z tego formantu.

### <a name="instances"></a>Wystąpienia

Ustaw właściwość **Count wystąpienia** na liczbę wystąpień, które usługa powinna uruchomić dla tej roli.

Ustaw właściwość **Rozmiar maszyny Wirtualnej** na **Bardzo mały,** **Mały,** **Średni,** **Duży**lub **Bardzo duży.**  Aby uzyskać więcej informacji, zobacz [Rozmiary usług Cloud Services](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Akcja uruchamiania (tylko rola sieci Web)

Ustaw tę właściwość, aby określić, że program Visual Studio należy uruchomić przeglądarkę sieci web dla punktów końcowych HTTP lub punktów końcowych HTTPS lub obu po uruchomieniu debugowania.

Opcja **punktu końcowego HTTPS** jest dostępna tylko wtedy, gdy zdefiniowano już punkt końcowy HTTPS dla swojej roli. Punkt końcowy HTTPS można zdefiniować na stronie właściwości **Punkty końcowe.**

Jeśli dodano już punkt końcowy HTTPS, opcja punktu końcowego HTTPS jest domyślnie włączona, a program Visual Studio uruchamia przeglądarkę dla tego punktu końcowego po uruchomieniu debugowania, oprócz przeglądarki dla punktu końcowego HTTP, przy założeniu, że obie opcje uruchamiania są włączone.

### <a name="diagnostics"></a>Diagnostyka

Domyślnie diagnostyka jest włączona dla roli sieci Web. Projekt usługi w chmurze platformy Azure i konto magazynu są ustawione na użycie emulatora magazynu lokalnego. Gdy wszystko będzie gotowe do wdrożenia na platformie Azure, możesz wybrać przycisk konstruktora (**...**), aby zamiast tego użyć magazynu platformy Azure. Dane diagnostyczne można przenieść na konto magazynu na żądanie lub w zaplanowanych automatycznie odstępach czasu. Aby uzyskać więcej informacji na temat diagnostyki platformy Azure, zobacz [Włączanie diagnostyki w usługach w chmurze i maszynach wirtualnych platformy Azure.](/azure/cloud-services/cloud-services-dotnet-diagnostics)

## <a name="settings-page"></a>Strona Ustawienia

Na stronie **Ustawienia** można dodać ustawienia do konfiguracji jako pary nazwa-wartość. Kod uruchomiony w roli można odczytać wartości ustawień konfiguracji w czasie wykonywania przy użyciu klas dostarczonych przez [bibliotekę zarządzaną platformy Azure](/previous-versions/azure/dn602775(v=azure.11)), w szczególności [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) metody.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Konfigurowanie ciągu połączenia dla konta magazynu

Parametry połączenia to ustawienie, które udostępnia informacje o połączeniu i uwierzytelnianiu dla emulatora magazynu lub konta magazynu platformy Azure. Ilekroć kod w roli uzyskuje dostęp do magazynu platformy Azure (obiekty blob, kolejki lub tabele), potrzebuje ciągu połączenia.

> [!Note]
> Parametry połączenia dla konta magazynu platformy Azure muszą używać zdefiniowanego formatu (zobacz [Konfigurowanie ciągów połączeń usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)).

Można ustawić parametry połączenia, aby w razie potrzeby używać magazynu lokalnego, a następnie ustawić konto magazynu platformy Azure podczas wdrażania aplikacji usługi w chmurze. Niepowodzenie prawidłowego ustawienia ciągu połączenia może spowodować, że rola nie rozpocznie się lub przejdzie przez stany inicjowania, zajętości i zatrzymywania.

Aby utworzyć parametry połączenia, wybierz pozycję **Dodaj ustawienie** i ustaw **typ** na "Parametry połączenia".

W przypadku nowych lub istniejących ciągów połączeń wybierz **...** * po prawej stronie pola **Wartość,** aby otworzyć okno dialogowe **Utwórz parametry połączenia magazynu:**

1. W obszarze **Połącz za pomocą**wybierz opcję **Twoja subskrypcja,** aby wybrać konto magazynu z subskrypcji. Visual Studio następnie uzyskuje poświadczenia konta magazynu `.publishsettings` automatycznie z pliku.
1. Wybranie **ręcznie wprowadzonych poświadczeń** umożliwia określenie nazwy konta i klucza bezpośrednio przy użyciu informacji z witryny Azure portal. Aby skopiować klucz konta:
    1. Przejdź do konta magazynu w witrynie Azure portal i wybierz pozycję **Zarządzaj kluczami**.
    1. Aby skopiować klucz konta, przejdź do konta magazynu w witrynie Azure Portal, wybierz **pozycję Ustawienia > klucze programu Access**, a następnie użyj przycisku kopiowania, aby skopiować podstawowy klucz dostępu do schowka.
1. Wybierz jedną z opcji połączenia. **Określ niestandardowe punkty końcowe** z prośbą o określenie określonych adresów URL dla obiektów blob, tabel i kolejek. Niestandardowe punkty końcowe umożliwiają korzystanie z [domen niestandardowych](/azure/storage/blobs/storage-custom-domain-name) i dokładniej kontrolować dostęp. Zobacz [Konfigurowanie ciągów połączeń usługi Azure Storage](/azure/storage/common/storage-configure-connection-string).
1. Wybierz **przycisk OK**, a następnie pozycję Plik > **Zapisz,** aby zaktualizować konfigurację za pomocą nowego ciągu połączenia.

Ponownie podczas publikowania aplikacji na platformie Azure wybierz konfigurację usługi, która zawiera konto magazynu platformy Azure dla ciągu połączenia. Po opublikowaniu aplikacji sprawdź, czy aplikacja działa zgodnie z oczekiwaniami względem usług magazynu platformy Azure.

Aby uzyskać więcej informacji na temat aktualizowania konfiguracji usługi, zobacz sekcję [Zarządzanie ciągami połączeń dla kont magazynu](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Strona Punkty końcowe

Rola sieci web zazwyczaj ma jeden punkt końcowy HTTP na porcie 80. Rola procesu roboczego, z drugiej strony, może mieć dowolną liczbę punktów końcowych HTTP, HTTPS lub TCP. Punkty końcowe mogą być wejściowe punkty końcowe, które są dostępne dla klientów zewnętrznych lub wewnętrznych punktów końcowych, które są dostępne dla innych ról, które są uruchomione w usłudze.

- Aby udostępnić punkt końcowy HTTP klientom zewnętrznym i przeglądarkom sieci Web, zmień typ punktu końcowego na dane wejściowe i określ nazwę i numer portu publicznego.
- Aby udostępnić punkt końcowy HTTPS klientom zewnętrznym i przeglądarkom sieci Web, zmień typ punktu końcowego na **wejściowy**i określ nazwę, numer portu publicznego i nazwę certyfikatu zarządzania. Przed określeniem certyfikatu zarządzania należy również zdefiniować certyfikat na stronie Właściwości **Certyfikaty.**
- Aby udostępnić punkt końcowy dla dostępu wewnętrznego przez inne role w usłudze w chmurze, zmień typ punktu końcowego na wewnętrzny i określ nazwę i możliwe porty prywatne dla tego punktu końcowego.

## <a name="local-storage-page"></a>Strona magazynu lokalnego

Za pomocą strony właściwości **Magazyn lokalny** można zarezerwować jeden lub więcej zasobów magazynu lokalnego dla roli. Zasób magazynu lokalnego jest zastrzeżonym katalogiem w systemie plików maszyny wirtualnej platformy Azure, w którym jest uruchomione wystąpienie roli.

## <a name="certificates-page"></a>Strona Certyfikaty

Strona właściwości **Certyfikaty** dodaje informacje o certyfikatach do konfiguracji usługi. Należy pamiętać, że certyfikaty nie są pakowane z usługą; należy przekazać certyfikaty oddzielnie na platformę Azure za pośrednictwem [witryny Azure portal](https://portal.azure.com).

Dodanie certyfikatu w tym miejscu dodaje informacje o certyfikatach do konfiguracji usługi. Certyfikaty nie są pakowane z usługą; należy przekazać certyfikaty oddzielnie za pośrednictwem witryny Azure portal.

Aby skojarzyć certyfikat z rolą, podaj nazwę certyfikatu. Ta nazwa służy do odwoływania się do certyfikatu podczas konfigurowania punktu końcowego HTTPS na stronie **Punkty końcowe.** Następnie określ, czy magazyn certyfikatów to **komputer lokalny** czy **bieżący użytkownik** oraz nazwa magazynu. Na koniec wprowadź odcisk palca certyfikatu. Jeśli certyfikat znajduje się w magazynie Bieżący użytkownik\Osobisty (Mój), można wprowadzić odcisk palca certyfikatu, wybierając certyfikat z listy wypełnionej. Jeśli znajduje się w innym miejscu, wprowadź wartość odcisku palca ręcznie.

Po dodaniu certyfikatu z magazynu certyfikatów wszystkie certyfikaty pośrednie są automatycznie dodawane do ustawień konfiguracji. Ponadto te certyfikaty pośrednie muszą zostać przekazane na platformę Azure, aby poprawnie skonfigurować usługę dla SSL.

Wszystkie certyfikaty zarządzania skojarzone z usługą mają zastosowanie do usługi tylko wtedy, gdy jest uruchomiona w chmurze. Gdy usługa jest uruchomiona w lokalnym środowisku programistycznym, używa standardowego certyfikatu, który jest zarządzany przez emulator obliczeń.
