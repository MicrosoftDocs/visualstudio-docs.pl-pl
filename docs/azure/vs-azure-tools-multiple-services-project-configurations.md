---
title: Konfigurowanie projektu platformy Azure przy użyciu wielu konfiguracji usługi
description: Dowiedz się, jak skonfigurować projekt usługi w chmurze platformy Azure, zmieniając plików ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg i ServiceConfiguration.Cloud.cscfg.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: dfb58c9eabb135b69033c065fa606511043a2c8b
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260647"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Konfigurowanie projektu platformy Azure w programie Visual Studio w celu używania wielu konfiguracji usługi

Projekt usługi w chmurze platformy Azure w programie Visual Studio zawiera trzy pliki konfiguracji: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg`, i `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` jest wdrażana na platformie Azure opisują wymagania dotyczące usługi w chmurze i jego role i skonfiguruj ustawienia, które są stosowane do wszystkich wystąpień. Ustawienia mogą być odczytywane w czasie wykonywania za pomocą usług obsługującego środowisko uruchomieniowe interfejsu API usługi Azure. Ten plik może zostać zaktualizowana na platformie Azure, tylko wtedy, gdy zatrzymaniu usługi w chmurze.
- `ServiceConfiguration.Local.cscfg` i `ServiceConfiguration.Cloud.cscfg` Podaj wartości dla ustawień w definicji plik i określ liczbę wystąpień do uruchamiania dla każdej roli. Plik "Local" zawiera wartości używane w debugowania lokalnego. Plik "Chmura" jest wdrożony na platformie Azure jako `ServiceConfiguration.cscfg` i udostępnia ustawienia w środowisku serwera. Ten plik może zostać zaktualizowana po uruchomieniu usługi w chmurze na platformie Azure.

Ustawienia konfiguracji są zarządzane i modyfikowane w programie Visual Studio za pomocą stron właściwości dla odpowiednich ról (kliknij prawym przyciskiem myszy rolę, a następnie wybierz pozycję **właściwości**, lub kliknij dwukrotnie roli). Zakres zmian niezależnie od konfiguracji jest wybierany w **konfiguracji usługi** listy rozwijanej. Właściwości dla ról sieć web i proces roboczy są podobne, z wyjątkiem w przypadku, gdy opisane w poniższych sekcjach.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Aby uzyskać informacji na temat podstawowych schematów dla definicji usługi i pliki konfiguracji usługi, zobacz [schemat XML .csdef](/azure/cloud-services/schema-csdef-file) i [schemat XML .cscfg](/azure/cloud-services/schema-cscfg-file) artykułów. Aby uzyskać więcej informacji na temat konfigurowania usługi zobacz [jak skonfigurować usługi w chmurze](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Strona konfiguracji

### <a name="service-configuration"></a>Konfiguracja usługi

Wybieranie, które `ServiceConfiguration.*.cscfg` pliku mają wpływ zmiany. Domyślnie są lokalne, jak i chmury, a następnie można użyć **Zarządzaj...**  polecenie, aby skopiować, zmiana nazwy i usuwanie plików konfiguracyjnych. Te pliki są dodawane do projektu usługi w chmurze i są wyświetlane w **Eksploratora rozwiązań**. Jednak zmiana nazwy lub usuwanie konfiguracji może odbywać się tylko z tego formantu.

### <a name="instances"></a>Wystąpienia

Ustaw **wystąpienia** policzyć liczbę wystąpień usługi, należy uruchomić dla tej roli.

Ustaw **rozmiar maszyny Wirtualnej** właściwości **wystąpieniom bardzo małe**, **małych**, **średni**, **duże**, lub **Bardzo duże**.  Aby uzyskać więcej informacji, zobacz [rozmiary usług Cloud Services](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Uruchamianie akcji (tylko w przypadku roli sieci Web)

Ustaw tę właściwość, aby określić, czy programu Visual Studio należy uruchomić przeglądarkę internetową punktów końcowych HTTP lub punktów końcowych HTTPS, czy oba rodzaje podczas uruchamiania debugowania.

**Punktu końcowego HTTPS** opcja jest dostępna tylko wtedy, gdy już zdefiniowano punktu końcowego HTTPS dla roli użytkownika. Można zdefiniować punkt końcowy HTTPS **punktów końcowych** stronę właściwości.

Jeśli masz już dodany punkt końcowy HTTPS, opcji punktu końcowego HTTPS jest domyślnie włączona, i Visual Studio otworzy w przeglądarce dla tego punktu końcowego podczas uruchamiania debugowania, oprócz przeglądarki dla punktu końcowego HTTP, przy założeniu, że obie opcje uruchamiania są włączone.

### <a name="diagnostics"></a>Diagnostyka

Domyślnie diagnostyki są włączone dla roli sieci Web. Konta projektu i magazynu usługi platformy Azure w chmurze są skonfigurowane do korzystania z emulatora magazynu lokalnego. Gdy wszystko jest gotowe do wdrożenia na platformie Azure, możesz wybrać przycisk konstruktora ( **...** ) zamiast tego użyć usługi Azure storage. Dane diagnostyczne mogą przesyłać do konta magazynu, na żądanie lub automatycznie zaplanowanych odstępach czasu. Aby uzyskać więcej informacji na temat usługi Diagnostyka Azure, zobacz [Włączanie diagnostyki w usługach Azure Cloud Services i Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Strona Ustawienia

Na **ustawienia** stronie ustawień konfiguracji, której można dodać jako pary nazwa wartość. Kod uruchomiony w roli można odczytać wartości ustawień konfiguracji w czasie wykonywania przy użyciu klas dostarczonych przez [biblioteki usługi Azure Managed](http://go.microsoft.com/fwlink?LinkID=171026), w szczególności [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx) metody.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Konfigurowanie parametrów połączenia dla konta magazynu

Parametry połączenia to ustawienie, które zapewnia połączenia i informacje dotyczące uwierzytelniania dla emulatora magazynu lub konta usługi Azure storage. Zawsze, gdy kod w roli uzyskuje dostęp do usługi Azure storage (obiekty BLOB, kolejki lub tabeli), wymaga parametrów połączenia.

> [!Note]
> Ciąg połączenia dla konta magazynu platformy Azure musi mieć zdefiniowany format (zobacz [skonfigurować parametry połączenia magazynu Azure](/azure/storage/common/storage-configure-connection-string)).

Można ustawić parametry połączenia do korzystania z magazynów lokalnych, zgodnie z potrzebami, a następnie ustaw na konto magazynu platformy Azure, w przypadku wdrażania aplikacji usługi w chmurze. Nie można poprawnie ustawić parametrów połączenia może spowodować Twojej roli nie można uruchomić lub przechodzić między Stanami inicjowanie, zajęta i zatrzymywanie.

Aby utworzyć parametry połączenia, wybierz **Dodaj ustawienie** i ustaw **typu** ciągowi"połączenia".

Dla parametrów połączenia w nowym lub istniejącym, wybierz **...** * po prawej stronie **wartość** pole, aby otworzyć **utworzyć parametry połączenia magazynu** okno dialogowe:

1. W obszarze **nawiązywanie połączenia przy użyciu**, wybierz **subskrypcji** opcję, aby wybrać konto magazynu z subskrypcji. Program Visual Studio następnie uzyskuje poświadczeń konta magazynu, który automatycznie z `.publishsettings` pliku.
1. Wybieranie **ręcznie wprowadzić poświadczenia** pozwala określić nazwę konta i klucza bezpośrednio przy użyciu informacji z witryny Azure portal. Aby skopiować klucz konta:
    1. Przejdź do konta magazynu w witrynie Azure portal i wybierz **zarządzanie kluczami**.
    1. Aby skopiować klucz konta, przejdź do konta magazynu w witrynie Azure portal, wybierz opcję **Ustawienia > klucze dostępu**, następnie użyj przycisku kopiowania, aby skopiuj podstawowy klucz dostępu do Schowka.
1. Wybierz jedną z opcji połączenia. **Określ niestandardowe punkty końcowe** prosi o określenie określonych adresów URL dla obiektów blob, tabele i kolejki. Niestandardowe punkty końcowe umożliwiają używanie [domen niestandardowych](/azure/storage/blobs/storage-custom-domain-name) i kontrolować dostęp do bardziej dokładnie. Zobacz [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string).
1. Wybierz **OK**, następnie **Plik > Zapisz** można zaktualizować konfiguracji za pomocą nowych parametrów połączenia.

Ponownie podczas publikowania aplikacji na platformie Azure, wybierz pozycję konfiguracji usługi, która zawiera konta usługi Azure storage dla parametrów połączenia. Po opublikowaniu aplikacji, sprawdź, czy aplikacja działa zgodnie z oczekiwaniami w odniesieniu do usług Azure storage.

Aby uzyskać więcej informacji o sposobie aktualizowania konfiguracji usługi, zobacz sekcję [Zarządzanie parametry połączenia dla konta magazynu](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Strona punkty końcowe

Rola internetowa zazwyczaj ma jeden punkt końcowy HTTP na porcie 80. Z drugiej strony, rolę procesu roboczego może mieć dowolną liczbę punktów końcowych HTTP, HTTPS lub TCP. Punkty końcowe można wejściowych punktów końcowych, które są dostępne dla klientów zewnętrznych, lub wewnętrznych punktów końcowych, które są dostępne dla innych ról, które działają w usłudze.

- Aby udostępnić punkt końcowy HTTP do klientów zewnętrznych i przeglądarki sieci Web, Zmień typ punktu końcowego na dane wejściowe, a następnie określ nazwę i numeru portu publicznego.
- Aby udostępnić punkt końcowy HTTPS do klientów zewnętrznych i przeglądarki sieci Web, należy zmienić typ punktu końcowego na **danych wejściowych**, a następnie określ nazwę, numeru portu publicznego i nazwa certyfikatu zarządzania. Należy także zdefiniować certyfikat na **certyfikaty** strony właściwości można było określić certyfikat zarządzania.
- Aby udostępnić punkt końcowy wewnętrznego dostępu przez inne role w usłudze w chmurze, Zmień typ punktu końcowego wewnętrznego i określ nazwę i możliwe prywatnej portów dla tego punktu końcowego.

## <a name="local-storage-page"></a>Strona magazynu lokalnego

Możesz użyć **Magazyn lokalny** stronę właściwości do rezerwowania co najmniej jeden zasób magazynu lokalnego dla roli. Zasób magazynu lokalnego jest zastrzeżony katalogu w systemie plików z maszyny wirtualnej platformy Azure, w którym jest uruchomione wystąpienie roli.

## <a name="certificates-page"></a>Strona certyfikaty

**Certyfikaty** strona właściwości dodaje informacje o certyfikatach do konfiguracji usługi. Należy pamiętać, że certyfikaty nie są w pakiecie przy użyciu usługi; należy przekazać certyfikaty oddzielnie na platformie Azure za pośrednictwem [witryny Azure portal](http://portal.azure.com).

Dodawanie certyfikatu w tym miejscu dodaje informacje o certyfikatach do konfiguracji usługi. Certyfikaty nie są opakowane w usłudze; należy przekazać certyfikaty oddzielnie za pośrednictwem witryny Azure portal.

Aby skojarzyć certyfikat z roli użytkownika, podaj nazwę dla certyfikatu. Nazwa ta będzie używana do odwoływania się do certyfikatu podczas konfigurowania punktu końcowego HTTPS w **punktów końcowych** strony. Następnie określ, czy magazyn certyfikatów znajduje się **komputera lokalnego** lub **bieżącego użytkownika** i nazwę magazynu. Na koniec wprowadź odcisk palca certyfikatu. Jeśli certyfikat znajduje się w bieżącym User\Personal magazynie (użytkownika), można wprowadzić odcisk palca certyfikatu, wybierając certyfikat z lista jest pusta. Jeśli znajduje się on w dowolnej innej lokalizacji, należy ręcznie wprowadzić wartość odcisku palca.

Po dodaniu certyfikatu z magazynu certyfikatów, wszystkie certyfikaty pośrednie są automatycznie dodawane do ustawień konfiguracji. Ponadto te certyfikaty pośrednie muszą być przesłane do platformy Azure, aby poprawnie skonfigurować usługę dla protokołu SSL.

Wszystkie certyfikaty zarządzania, które kojarzą przy użyciu usługi mają zastosowanie do usługi, tylko wtedy, gdy jest uruchomiona w chmurze. Gdy usługa jest uruchomiona w lokalne Środowisko deweloperskie, używa to standardowy certyfikat, który jest zarządzany przez emulator obliczeń.
