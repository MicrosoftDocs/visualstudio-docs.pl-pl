---
title: Konfigurowanie projektu platformy Azure z wieloma konfiguracjami usługi
description: Dowiedz się, jak skonfigurować projekt usługi w chmurze platformy Azure, zmieniając pliki ServiceDefinition. csdef, ServiceConfiguration. local. cscfg i ServiceConfiguration. Cloud. cscfg.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 8c9f65291d43a55ee75840591698c26fdde6e967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85280547"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Konfigurowanie projektu platformy Azure w programie Visual Studio w celu używania wielu konfiguracji usługi

Projekt usługi w chmurze platformy Azure w programie Visual Studio zawiera trzy pliki konfiguracji: `ServiceDefinition.csdef` , `ServiceConfiguration.Local.cscfg` i `ServiceConfiguration.Cloud.cscfg` :

- `ServiceDefinition.csdef` Program został wdrożony na platformie Azure, aby opisać wymagania usługi w chmurze i jej ról oraz zapewnić ustawienia, które mają zastosowanie do wszystkich wystąpień. Ustawienia można odczytać w czasie wykonywania za pomocą interfejsu API środowiska uruchomieniowego hostingu usług platformy Azure. Ten plik można zaktualizować na platformie Azure tylko wtedy, gdy usługa w chmurze jest zatrzymana.
- `ServiceConfiguration.Local.cscfg` i `ServiceConfiguration.Cloud.cscfg` podaj wartości ustawień w pliku definicji i określ liczbę wystąpień do uruchomienia dla każdej roli. Plik "Local" zawiera wartości używane w debugowaniu lokalnym; plik "Cloud" został wdrożony na platformie Azure jako `ServiceConfiguration.cscfg` i zawiera ustawienia dla środowiska serwera. Ten plik można zaktualizować, gdy usługa w chmurze jest uruchomiona na platformie Azure.

Ustawienia konfiguracji są zarządzane i modyfikowane w programie Visual Studio przy użyciu stron właściwości dla odpowiedniej roli (kliknij prawym przyciskiem myszy rolę i wybierz pozycję **Właściwości**lub kliknij dwukrotnie rolę). Zmiany mogą być ograniczone do zakresu konfiguracji wybranej na liście rozwijanej **Konfiguracja usługi** . Właściwości ról Sieć Web i proces roboczy są podobne, z wyjątkiem przypadków opisanych w poniższych sekcjach.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Aby uzyskać informacje na temat podstawowych schematów dla plików definicji usługi i konfiguracji usługi, zobacz artykuł [. CSDEF XML](/azure/cloud-services/schema-csdef-file) schematu i [. cscfg — artykuły schematu XML](/azure/cloud-services/schema-cscfg-file) . Aby uzyskać więcej informacji na temat konfiguracji usługi, zobacz [jak skonfigurować Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Strona konfiguracji

### <a name="service-configuration"></a>Konfiguracja usługi

Wybiera `ServiceConfiguration.*.cscfg` plik, na który mają wpływ zmiany. Domyślnie istnieją zarówno odmiany lokalne, jak i w chmurze, a także można użyć polecenia **Zarządzaj...** , aby skopiować, zmienić nazwę i usunąć pliki konfiguracji. Te pliki są dodawane do projektu usługi w chmurze i pojawiają się w **Eksplorator rozwiązań**. Zmiany nazw lub usuwania konfiguracji można jednak wykonać tylko z tego formantu.

### <a name="instances"></a>Wystąpienia

Ustaw właściwość liczba **wystąpień** na liczbę wystąpień, które usługa powinna uruchomić dla tej roli.

Ustaw właściwość **rozmiar maszyny wirtualnej** na **bardzo małe**, **małe**, **średnie**, **duże**lub **bardzo duże**.  Aby uzyskać więcej informacji, zobacz [Rozmiary usług Cloud Services](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Akcja uruchamiania (tylko rola sieci Web)

Ustaw tę właściwość, aby określić, że program Visual Studio ma uruchamiać przeglądarkę internetową dla punktów końcowych HTTP lub punktów końcowych HTTPS, albo podczas uruchamiania debugowania.

Opcja **punktu końcowego HTTPS** jest dostępna tylko wtedy, gdy masz już zdefiniowany punkt końcowy HTTPS dla roli. Punkt końcowy HTTPS można zdefiniować na stronie właściwości **punkty końcowe** .

Jeśli dodano już punkt końcowy HTTPS, opcja punktu końcowego HTTPS jest domyślnie włączona, a program Visual Studio uruchamia przeglądarkę dla tego punktu końcowego po rozpoczęciu debugowania, poza przeglądarką punktu końcowego HTTP, przy założeniu, że oba opcje uruchamiania są włączone.

### <a name="diagnostics"></a>Diagnostyka

Domyślnie Diagnostyka jest włączona dla roli sieci Web. Projekt usługi w chmurze platformy Azure i konto magazynu są ustawione tak, aby używały lokalnego emulatora magazynu. Gdy wszystko będzie gotowe do wdrożenia na platformie Azure, możesz wybrać przycisk konstruktora (**...**), aby użyć usługi Azure Storage. Dane diagnostyczne można transferować do konta magazynu na żądanie lub w automatycznie zaplanowanych odstępach czasu. Aby uzyskać więcej informacji na temat diagnostyki platformy Azure, zobacz [Włączanie diagnostyki na platformie azure Cloud Services i Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Strona Ustawienia

Na stronie **Ustawienia** można dodać ustawienia do konfiguracji jako pary nazwa-wartość. Kod uruchomiony w roli może odczytywać wartości ustawień konfiguracji w czasie wykonywania przy użyciu klas udostępnianych przez [bibliotekę zarządzaną platformy Azure](/previous-versions/azure/dn602775(v=azure.11)), w tym w ramach metody [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) .

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Konfigurowanie parametrów połączenia dla konta magazynu

Parametry połączenia to ustawienie, które zapewnia informacje o połączeniu i uwierzytelnianiu dla emulatora magazynu lub dla konta usługi Azure Storage. Za każdym razem, gdy kod w roli uzyskuje dostęp do usługi Azure Storage (obiektów blob, kolejek lub tabel), potrzebuje parametrów połączenia.

> [!Note]
> Parametry połączenia dla konta usługi Azure Storage muszą mieć zdefiniowany format (zobacz [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)).

Możesz ustawić parametry połączenia tak, aby używały magazynu lokalnego, a następnie ustawić konto usługi Azure Storage podczas wdrażania aplikacji w usłudze w chmurze. Nie można prawidłowo ustawić parametrów połączenia, które mogą spowodować, że nie można uruchomić roli lub aby przejść przez Stany inicjowania, zajętości i zatrzymywania.

Aby utworzyć parametry połączenia, wybierz opcję **Dodaj ustawienie** i ustaw **typ** na "parametry połączenia".

W przypadku nowych lub istniejących parametrów połączenia wybierz pozycję **...** * po prawej stronie pola **wartość** , aby otworzyć okno dialogowe **Tworzenie parametrów połączenia magazynu** :

1. W obszarze **Połącz przy użyciu**wybierz opcję **subskrypcja** , aby wybrać konto magazynu z subskrypcji. Program Visual Studio następnie automatycznie uzyskuje poświadczenia konta magazynu z `.publishsettings` pliku.
1. Wybranie pozycji **Ręczne wprowadzanie poświadczeń** pozwala określić nazwę konta i klucz bezpośrednio przy użyciu informacji z Azure Portal. Aby skopiować klucz konta:
    1. Przejdź do konta magazynu na Azure Portal a następnie wybierz pozycję **Zarządzaj kluczami**.
    1. Aby skopiować klucz konta, przejdź do konta magazynu w Azure Portal, wybierz pozycję **ustawienia > klucze dostępu**, a następnie użyj przycisku kopiowania, aby skopiować podstawowy klucz dostępu do Schowka.
1. Wybierz jedną z opcji połączenia. **Określ niestandardowe punkty końcowe** z prośbą o określenie określonych adresów URL dla obiektów blob, tabel i kolejek. Niestandardowe punkty końcowe umożliwiają korzystanie z [domen niestandardowych](/azure/storage/blobs/storage-custom-domain-name) i precyzyjne kontrolowanie dostępu. Zobacz [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string).
1. Wybierz przycisk **OK**, a następnie **plik > Zapisz** , aby zaktualizować konfigurację przy użyciu nowych parametrów połączenia.

Po opublikowaniu aplikacji na platformie Azure wybierz konfigurację usługi, która zawiera konto usługi Azure Storage dla parametrów połączenia. Po opublikowaniu aplikacji Sprawdź, czy aplikacja działa zgodnie z oczekiwaniami w odniesieniu do usług Azure Storage.

Więcej informacji o sposobach aktualizowania konfiguracji usługi znajduje się w sekcji [Zarządzanie ciągami połączenia dla kont magazynu](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Strona punkty końcowe

Rola sieci Web zazwyczaj ma jeden punkt końcowy HTTP na porcie 80. Rola procesu roboczego, z drugiej strony, może mieć dowolną liczbę punktów końcowych HTTP, HTTPS lub TCP. Punkty końcowe mogą być wejściowymi punktami końcowymi, które są dostępne dla klientów zewnętrznych lub wewnętrznych punktów końcowych, które są dostępne dla innych ról uruchomionych w usłudze.

- Aby udostępnić punkt końcowy HTTP klientom zewnętrznym i przeglądarkom sieci Web, Zmień typ punktu końcowego na wejściowy, a następnie podaj nazwę i numer portu publicznego.
- Aby udostępnić punkt końcowy HTTPS klientom zewnętrznym i przeglądarkom sieci Web, Zmień typ punktu końcowego na **wejściowy**, a następnie określ nazwę, numer portu publicznego i nazwę certyfikatu zarządzania. Należy również zdefiniować certyfikat na stronie właściwości **Certyfikaty** , aby można było określić certyfikat zarządzania.
- Aby udostępnić punkt końcowy dla dostępu wewnętrznego przez inne role w usłudze w chmurze, Zmień typ punktu końcowego na wewnętrzny i określ nazwę i możliwe porty prywatne dla tego punktu końcowego.

## <a name="local-storage-page"></a>Strona magazynu lokalnego

Korzystając ze strony właściwości **magazynu lokalnego** , można zarezerwować jeden lub więcej zasobów magazynu lokalnego dla roli. Lokalny zasób magazynu jest katalogiem zastrzeżonym w systemie plików maszyny wirtualnej platformy Azure, w którym jest uruchomiona wystąpienie roli.

## <a name="certificates-page"></a>Strona Certyfikaty

Strona właściwości **Certyfikaty** umożliwia dodanie informacji o certyfikatach do konfiguracji usługi. Należy pamiętać, że certyfikaty nie są pakowane z usługą; certyfikaty należy przekazać osobno na platformę Azure za pomocą [Azure Portal](https://portal.azure.com).

Dodanie tutaj certyfikatu powoduje dodanie informacji o certyfikatach do konfiguracji usługi. Certyfikaty nie są pakowane z usługą; certyfikaty należy przekazać oddzielnie za pomocą Azure Portal.

Aby skojarzyć certyfikat z rolą, podaj nazwę certyfikatu. Ta nazwa jest używana do odwoływania się do certyfikatu podczas konfigurowania punktu końcowego HTTPS na stronie **punkty końcowe** . Następnie określ, czy magazyn certyfikatów jest **komputerem lokalnym** , czy **bieżącym użytkownikiem** i nazwą magazynu. Na koniec wprowadź odcisk palca certyfikatu. Jeśli certyfikat znajduje się w bieżącym magazynie User\Personal (my), możesz wprowadzić odcisk palca certyfikatu, wybierając certyfikat z wypełnionej listy. Jeśli znajduje się w innej lokalizacji, wprowadź wartość odcisku palca ręcznie.

Po dodaniu certyfikatu z magazynu certyfikatów wszystkie certyfikaty pośrednie są automatycznie dodawane do ustawień konfiguracji. Ponadto te certyfikaty pośrednie muszą zostać przekazane do platformy Azure w celu poprawnego skonfigurowania usługi na potrzeby protokołu SSL.

Wszystkie certyfikaty zarządzania powiązane z usługą mają zastosowanie tylko w przypadku, gdy jest uruchomiona w chmurze. Gdy usługa jest uruchomiona w lokalnym środowisku programistycznym, korzysta z standardowego certyfikatu zarządzanego przez emulator obliczeń.
