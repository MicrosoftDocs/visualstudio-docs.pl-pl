---
title: Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1b52628b016893353c83e998a1e395118807a31
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603918"
---
# <a name="access-local-and-remote-data-in-clickonce-applications"></a>Dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce
Większość aplikacji tworzą lub wykorzystują dane. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapewnia różne opcje do odczytywania i zapisywania danych, zarówno lokalnie, jak i zdalnie.

## <a name="local-data"></a>Dane lokalne
 Za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], możesz załadować i przechowywać dane lokalnie, używając jednej z następujących metod:

- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Data Directory

- Izolowany magazyn

- Inne pliki lokalne

### <a name="clickonce-data-directory"></a>Katalog danych ClickOnce
 Każdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zainstalowanej na komputerze lokalnym ma katalog danych, przechowywany w katalogu Documents and Settings użytkownika. Każdy plik objęte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i oznaczony jako plik "dane" jest kopiowany do tego katalogu, gdy aplikacja jest zainstalowana. Pliki danych może być dowolnego typu pliku, najczęściej używane są tekstu, XML i pliki bazy danych, takich jak pliki .mdb Microsoft Access.

 Katalog danych jest przeznaczona dla danych zarządzanych aplikacji, które to dane, które aplikacja jawnie zapisuje i przechowuje. Wszystkie statyczne nondependency pliki nie są oznaczone jako "dane" w manifeście aplikacji będzie zamiast tego znajdują się w katalogu aplikacji. Jest to katalog, gdzie aplikacja pliku wykonywalnym (*.exe*) znajdują się pliki oraz zestawy.

> [!NOTE]
>  Gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] odinstalowania aplikacji, katalog danych zostaną również usunięte. Nie wolno używać katalogu danych do przechowywania danych zarządzanych przez użytkowników końcowych, takich jak dokumenty.

#### <a name="mark-data-files-in-a-clickonce-distribution"></a>Oznacz pliki danych w dystrybucji ClickOnce
 Aby przełączyć istniejącego pliku w katalogu danych, należy oznaczyć istniejący plik jako plik danych w Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliku manifestu aplikacji aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

#### <a name="read-from-and-write-to-the-data-directory"></a>Odczytywanie i zapisywanie do katalogu danych
 Odczytywanie ich z katalogu danych wymaga, aby Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] żądanie aplikacji uprawnienia do odczytu; podobnie zapisu do katalogu wymaga uprawnień do zapisu. Aplikacja będzie automatycznie mają to uprawnienie, jeśli jest skonfigurowany do uruchamiania przy użyciu pełnego zaufania. Aby uzyskać więcej informacji na temat wzrasta uprawnień dla aplikacji przy użyciu zaufanego wdrożenia aplikacji lub podnoszenia poziomu uprawnień, zobacz [aplikacji Secure ClickOnce](../deployment/securing-clickonce-applications.md).

> [!NOTE]
>  Jeśli Twoja organizacja nie korzysta z zaufanego wdrożenia aplikacji i została wyłączona podnoszenia poziomu uprawnień, Potwierdzanie uprawnienia zakończy się niepowodzeniem.

 Po aplikacja ma te uprawnienia, go uzyskać dostęp do katalogu danych za pomocą wywołań metod w klasach w ramach <xref:System.IO>. Możesz uzyskać ścieżkę katalogu danych w formularzach Windows [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację za pomocą <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> właściwości zdefiniowane w <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> właściwość <xref:System.Deployment.Application.ApplicationDeployment>. Jest to wygodne i najbardziej zalecany sposób uzyskiwać dostęp do danych. Poniższy przykład kodu pokazuje, jak to zrobić w pliku tekstowym o nazwie *CSV.txt* zawierającego w danym wdrożeniu, jak plik danych.

 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]

 Aby uzyskać więcej informacji na temat oznaczanie plików w danym wdrożeniu jako pliki danych, zobacz [jak: Uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

 Możesz również uzyskać ścieżkę katalogu danych przy użyciu odpowiednich zmiennych na <xref:System.Windows.Forms.Application> klasy, takie jak <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.

 Manipulowanie inne typy plików mogą wymagać dodatkowych uprawnień. Na przykład, jeśli chcesz używać bazy danych programu Access (*.mdb*) pliku, aplikacja musi assert pełne zaufanie aby można było używać odpowiedniego \<xref:System.Data > klasy.

#### <a name="data-directory-and-application-versions"></a>Katalog danych i wersji aplikacji
 Każda wersja aplikacji ma swój własny katalog danych, która jest odizolowana od innych wersji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzy ten katalog, niezależnie od tego, czy wszystkie pliki danych są uwzględnione we wdrożeniu, tak, aby aplikacja ma lokalizację, aby utworzyć nowe pliki danych w czasie wykonywania. Po zainstalowaniu nowej wersji aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] skopiuje wszystkie istniejące pliki danych z poprzedniej wersji danych katalogu w katalogu danych nowej wersji — tego, czy zostały uwzględnione we wdrożeniu, oryginalnym lub utworzone przez aplikacja.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spowoduje zastąpienie starszą wersję pliku z nowszą wersją serwera, jeśli plik danych ma wartość różne wartości skrótów w starej wersji aplikacji, tak jak w nowej wersji. Ponadto jeśli starszą wersję aplikacji utworzony nowy plik, który ma taką samą nazwę jako plik uwzględnione we wdrożeniu nowej wersji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zastąpi starą wersję pliku za pomocą nowego pliku. W obu przypadkach stare pliki zostaną uwzględnione w podkatalogu w katalogu danych o nazwie `.pre`, dzięki czemu aplikacja może nadal uzyskiwać dostęp do starych danych dla celów migracji.

 Jeśli potrzebujesz bardziej szczegółowej migracji danych, możesz użyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania interfejsu API, aby przeprowadzić migrację niestandardowe z katalogu stare dane do nowego katalogu danych. Należy przetestować do pobrania dostępne przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, pobrać aktualizację, korzystając <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> lub <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>, a następnie wykonaj wszelkie niestandardowe migracji danych, pracy w własne po aktualizacji zostało zakończone.

### <a name="isolated-storage"></a>Wydzielona pamięć masowa
 Wydzielona pamięć masowa zapewnia interfejs API do tworzenia i uzyskiwania dostępu do plików za pomocą prostego interfejsu API. Rzeczywistej lokalizacji przechowywanych plików jest ukryty dla deweloperów i użytkownika.

 Izolowany magazyn działa we wszystkich wersjach [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Wydzielona pamięć masowa działa również w częściowo zaufanych aplikacji bez konieczności stosowania dodatkowych uprawnień przyznaje. Jeśli aplikacja musi działać w częściowej relacji zaufania, ale musi przechowywać dane specyficzne dla aplikacji, należy używać wydzielonej pamięci masowej.

 Aby uzyskać więcej informacji, zobacz [wydzielonej pamięci masowej](/dotnet/standard/io/isolated-storage).

### <a name="other-local-files"></a>Inne pliki lokalne
 Jeśli aplikacja musi działać z lub zapisu danych przez użytkownika końcowego, takie jak raporty, obrazy, muzyka i tak dalej, aplikacja będzie wymagać <xref:System.Security.Permissions.FileIOPermission> do odczytu i zapisu danych do lokalnego systemu plików.

## <a name="remote-data"></a>Dane zdalne
 W pewnym momencie aplikacja prawdopodobnie będzie mieć do pobierania informacji ze zdalnej witryny sieci Web, takie jak informacje o danych lub rynku klienta. W tej sekcji omówiono najbardziej typowe techniki pobierania zdalnych danych.

### <a name="access-files-with-http"></a>Dostęp do plików za pośrednictwem protokołu HTTP
 Dostępne dane z serwera sieci Web przy użyciu <xref:System.Net.WebClient> lub <xref:System.Net.HttpWebRequest> klasy w <xref:System.Net> przestrzeni nazw. Dane mogą być albo pliki statyczne lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacje, które zwracają nieprzetworzony tekst lub dane XML. Jeśli dane są w formacie XML, najszybszym sposobem pobrania danych polega na użyciu <xref:System.Xml.XmlDocument> klasy, których <xref:System.Xml.XmlDocument.Load%2A> metoda przyjmuje adres URL jako argument. Aby uzyskać przykład, zobacz [odczytu dokumentu XML do modelu DOM](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).

 Należy wziąć pod uwagę zabezpieczeń, gdy aplikacja uzyskuje dostęp do danych zdalnych za pośrednictwem protokołu HTTP. Domyślnie Twoja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji dostęp do zasobów sieciowych może być ograniczona, w zależności od tego, jak Twoja aplikacja została wdrożona. Te ograniczenia są stosowane do zapobiegania złośliwych programów, uzyskiwanie dostępu do uprzywilejowanych danych zdalnych lub do atakowania innych komputerów w sieci za pomocą komputera użytkownika.

 Poniższa tabela zawiera listę strategii wdrażania, których można użyć i ich domyślne uprawnienia sieci Web.

|Typ wdrożenia|Domyślne uprawnienia sieciowe|
|---------------------|---------------------------------|
|Instalacja w sieci Web|Dostęp tylko do serwera sieci Web, w którym aplikacja została zainstalowana|
|Instalowanie udziału plików|Nie można uzyskać dostępu serwerom sieci Web|
|Instalacja z dysku CD-ROM|Mają dostęp do dowolnego serwera sieci Web|

 Jeśli Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja nie może uzyskiwać dostęp do serwera sieci Web, z powodu ograniczeń zabezpieczeń, aplikacja musi assert <xref:System.Net.WebPermission> dla tej witryny sieci Web. Aby uzyskać więcej informacji na temat zwiększania uprawnień zabezpieczeń dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, zobacz [aplikacji Secure ClickOnce](../deployment/securing-clickonce-applications.md).

### <a name="access-data-through-an-xml-web-service"></a>Dostęp do danych za pośrednictwem usługi XML sieci Web
 Jeśli udostępnisz danych jako usługi sieci Web XML, uzyskujesz dostęp do danych za pomocą serwera proxy usługi sieci Web XML. Serwer proxy jest [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] utworzyć przy użyciu klasy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Operacje usługi XML sieci Web — takie jak pobieranie klientów, wprowadzanie do zamówienia i tak dalej — są widoczne jako metody na serwerze proxy. To sprawia, że usługi sieci Web łatwiejsze w użyciu niż nieprzetworzony tekst lub pliki XML.

 Jeśli usługi XML sieci Web działa za pośrednictwem protokołu HTTP, usługi będą powiązane przez te same ograniczenia zabezpieczeń jako <xref:System.Net.WebClient> i <xref:System.Net.HttpWebRequest> klasy.

### <a name="access-a-database-directly"></a>Bezpośredni dostęp do bazy danych
 Można użyć klas w obrębie <xref:System.Data> przestrzeń nazw w celu nawiązania bezpośredniego połączenia z serwerem bazy danych, takich jak program SQL Server w sieci, ale muszą uwzględniać związane z zabezpieczeniami. W przeciwieństwie do żądania HTTP żądania połączeń bazy danych są zawsze jest zabronione domyślnie w częściowej relacji zaufania; użytkownik będzie miał tylko takie uprawnienia domyślnie po zainstalowaniu usługi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji z dysku CD. Dzięki temu Twoja aplikacja pełnego zaufania. Aby umożliwić dostęp do konkretnej bazy danych programu SQL Server, należy zażądać aplikacji <xref:System.Data.SqlClient.SqlClientPermission> do niego; aby umożliwić dostęp do bazy danych innych niż SQL Server, należy zażądać <xref:System.Data.OleDb.OleDbPermission>.

 W większości przypadków, możesz nie mają dostępu do bazy danych bezpośrednio, ale zostanie do niego dostęp zamiast za pośrednictwem aplikacji serwera sieci Web napisane w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] lub usługi sieci Web XML. Uzyskiwanie dostępu do bazy danych w ten sposób jest często najlepszą metodę Jeśli Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest wdrażana z serwera sieci Web. Można korzystać z serwera, w częściowej relacji zaufania, bez podnoszenia uprawnień uprawnień aplikacji.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)