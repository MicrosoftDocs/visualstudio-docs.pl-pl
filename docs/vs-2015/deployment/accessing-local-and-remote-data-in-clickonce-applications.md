---
title: Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce6b6ee633e926709b0c15c2234077055600a07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688113"
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Większość aplikacji zużywa lub tworzy dane. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] oferuje różne opcje odczytu i zapisu danych, zarówno lokalnie, jak i zdalnie.  
  
## <a name="local-data"></a>Dane lokalne  
 Za pomocą programu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] można ładować i przechowywać dane lokalnie przy użyciu jednej z następujących metod:  
  
- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Katalog danych  
  
- Izolowany magazyn  
  
- Inne pliki lokalne  
  
### <a name="clickonce-data-directory"></a>Katalog danych ClickOnce  
 Każda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja zainstalowana na komputerze lokalnym ma katalog danych przechowywany w folderze dokumenty i ustawienia użytkownika. Każdy plik dołączony do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji i oznaczony jako plik "Data" jest kopiowany do tego katalogu podczas instalowania aplikacji. Pliki danych mogą być dowolnego typu plików, najczęściej używanymi plikami tekstowymi, XML i bazami danych, takimi jak pliki Microsoft Access. mdb.  
  
 Katalog danych jest przeznaczony dla danych zarządzanych przez aplikacje, które są danymi, które są w sposób jawny przechowywane i utrzymywane przez aplikację. Wszystkie statyczne, niezależne pliki, które nie są oznaczone jako "dane" w manifeście aplikacji, będą znajdować się w katalogu aplikacji. Ten katalog jest miejscem, w którym znajdują się pliki wykonywalne (. exe) aplikacji.  
  
> [!NOTE]
> Po [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] odinstalowaniu aplikacji jego katalog danych również jest usuwany. Nigdy nie używaj katalogu danych do przechowywania danych zarządzanych przez użytkownika końcowego, takich jak dokumenty.  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>Oznaczanie plików danych w dystrybucji ClickOnce  
 Aby umieścić istniejący plik w katalogu danych, należy oznaczyć istniejący plik jako plik danych w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pliku manifestu aplikacji aplikacji. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Dołączanie pliku danych do aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>Odczytywanie z i zapisywanie do katalogu danych  
 Odczytywanie z katalogu danych wymaga, aby [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja żądała uprawnienia do odczytu; podobnie zapis do katalogu wymaga uprawnień do zapisu. Aplikacja automatycznie będzie mieć to uprawnienie, jeśli jest skonfigurowana do uruchamiania z pełnym zaufaniem. Aby uzyskać więcej informacji na temat podnoszenia uprawnień do aplikacji przy użyciu podniesienia uprawnień lub zaufanego wdrożenia aplikacji, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
> Jeśli w organizacji nie jest używane wdrożenie zaufanej aplikacji i wyłączono podniesienie uprawnień, uprawnienia potwierdzania zakończą się niepowodzeniem.  
  
 Gdy aplikacja ma te uprawnienia, może uzyskać dostęp do katalogu danych za pomocą wywołań metod w klasach w ramach <xref:System.IO> . Ścieżkę do katalogu danych w aplikacji Windows Forms można uzyskać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> właściwości zdefiniowanej we <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> właściwości <xref:System.Deployment.Application.ApplicationDeployment> . Jest to najbardziej wygodny i zalecany sposób uzyskiwania dostępu do danych. Poniższy przykład kodu demonstruje, jak to zrobić dla pliku tekstowego o nazwie CSV.txt, który został uwzględniony w wdrożeniu jako plik danych.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.OpenDataFile/CS/Form1.cs#1)]
 [!code-vb[ClickOnce.OpenDataFile#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.OpenDataFile/VB/Form1.vb#1)]  
  
 Aby uzyskać więcej informacji na temat oznaczania plików we wdrożeniu jako plików danych, zobacz [jak to zrobić: Dołączanie pliku danych do aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 Możesz również uzyskać ścieżkę katalogu danych przy użyciu odpowiednich zmiennych w <xref:System.Windows.Forms.Application> klasie, takich jak <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A> .  
  
 Manipulowanie innymi typami plików może wymagać dodatkowych uprawnień. Na przykład, jeśli chcesz użyć pliku bazy danych programu Access (mdb), aplikacja musi zapewnić pełne zaufanie, aby można było korzystać z odpowiednich <xref:System.Data> klas.  
  
#### <a name="data-directory-and-application-versions"></a>Wersje katalogu i aplikacji  
 Każda wersja aplikacji ma swój własny katalog danych, który jest odizolowany od innych wersji. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tworzy ten katalog bez względu na to, czy pliki danych są uwzględniane we wdrożeniu, aby aplikacja była lokalizacją do tworzenia nowych plików danych w czasie wykonywania. Po zainstalowaniu nowej wersji aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Program skopiuje wszystkie istniejące pliki danych z katalogu danych poprzedniej wersji do katalogu danych nowej wersji — bez względu na to, czy zostały one uwzględnione w oryginalnym wdrożeniu, czy utworzone przez aplikację.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] spowoduje zastąpienie starszej wersji pliku nowszą wersją serwera, jeśli plik danych ma inną wartość skrótu w starej wersji aplikacji, jak w nowej wersji. Ponadto jeśli wcześniejsza wersja aplikacji utworzyła nowy plik o takiej samej nazwie jak plik uwzględniony w wdrożeniu nowej wersji, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] program zastąpi plik starej wersji nowym plikiem. W obu przypadkach stare pliki zostaną uwzględnione w podkatalogu w katalogu danych o nazwie `.pre` , dzięki czemu aplikacja będzie mogła uzyskać dostęp do starych danych na potrzeby migracji.  
  
 Jeśli potrzebujesz bardziej szczegółowej migracji danych, możesz użyć [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] interfejsu API wdrażania do przeprowadzenia niestandardowej migracji ze starego katalogu danych do nowego katalogu danych. Konieczne będzie przetestowanie dostępnego pobrania przy użyciu programu <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A> , pobranie aktualizacji przy użyciu programu <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> lub <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A> i wykonanie dowolnej niestandardowej migracji danych po zakończeniu aktualizacji.  
  
### <a name="isolated-storage"></a>Izolowany magazyn  
 Magazyn izolowany udostępnia interfejs API służący do tworzenia plików i uzyskiwania do nich dostępu przy użyciu prostego interfejsu API. Rzeczywista lokalizacja przechowywanych plików jest ukryta zarówno dla deweloperów, jak i dla użytkownika.  
  
 Magazyn izolowany działa we wszystkich wersjach programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Magazyn izolowany działa również w częściowo zaufanych aplikacjach bez konieczności stosowania dodatkowych uprawnień. Należy używać izolowanego magazynu, jeśli aplikacja musi działać w częściowej relacji zaufania, ale musi obsługiwać dane specyficzne dla aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [izolowany magazyn](https://msdn.microsoft.com/library/aff939d7-9e49-46f2-a8cd-938d3020e94e).  
  
### <a name="other-local-files"></a>Inne pliki lokalne  
 Jeśli aplikacja musi współpracować z danymi użytkowników końcowych, takimi jak raporty, obrazy, muzyka i tak dalej, aplikacja będzie wymagała <xref:System.Security.Permissions.FileIOPermission> odczytu i zapisu danych w lokalnym systemie plików.  
  
## <a name="remote-data"></a>Dane zdalne  
 W pewnym momencie aplikacja prawdopodobnie będzie musiała pobrać informacje ze zdalnej witryny sieci Web, na przykład dane klienta lub informacje o rynku. W tej sekcji omówiono najpopularniejsze techniki pobierania danych zdalnych.  
  
### <a name="accessing-files-by-using-http"></a>Uzyskiwanie dostępu do plików przy użyciu protokołu HTTP  
 Dostęp do danych z serwera sieci Web można uzyskać przy użyciu <xref:System.Net.WebClient> albo <xref:System.Net.HttpWebRequest> klasy w <xref:System.Net> przestrzeni nazw. Dane mogą być plikami statycznymi lub [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacjami, które zwracają nieprzetworzone dane tekstowe lub XML. Jeśli dane są w formacie XML, najszybszym sposobem na pobranie danych jest użycie <xref:System.Xml.XmlDocument> klasy, której <xref:System.Xml.XmlDocument.Load%2A> Metoda przyjmuje adres URL jako argument. Aby zapoznać się z przykładem, zobacz [odczytywanie dokumentu XML w modelu dom](https://msdn.microsoft.com/library/a4fb291f-5630-49ba-a49a-5b66c3b71e49).  
  
 Należy wziąć pod uwagę zabezpieczenia, gdy aplikacja uzyskuje dostęp do zdalnych danych za pośrednictwem protokołu HTTP. Domyślnie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dostęp do zasobów sieciowych może być ograniczony w zależności od sposobu wdrożenia aplikacji. Te ograniczenia są stosowane, aby uniemożliwić złośliwym programom uzyskanie dostępu do uprzywilejowanych danych zdalnych lub użycie komputera użytkownika w celu ataku na inne komputery w sieci.  
  
 W poniższej tabeli wymieniono strategie wdrażania, których można użyć, oraz ich domyślne uprawnienia sieci Web.  
  
|Typ wdrożenia|Domyślne uprawnienia sieciowe|  
|---------------------|---------------------------------|  
|Instalacja sieci Web|Może uzyskać dostęp tylko do serwera sieci Web, z którego została zainstalowana aplikacja|  
|Instalacja udziału plików|Nie można uzyskać dostępu do żadnych serwerów sieci Web|  
|Instalacja stacji CD-ROM|Może uzyskać dostęp do dowolnych serwerów sieci Web|  
  
 Jeśli [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja nie może uzyskać dostępu do serwera sieci Web ze względu na ograniczenia zabezpieczeń, aplikacja musi zostać potwierdzona <xref:System.Net.WebPermission> dla tej witryny sieci Web. Aby uzyskać więcej informacji na temat zwiększania uprawnień zabezpieczeń dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
### <a name="accessing-data-through-an-xml-web-service"></a>Uzyskiwanie dostępu do danych za poorednictwem usługi sieci Web XML  
 Jeśli dane są uwidaczniane jako usługa sieci Web XML, można uzyskać dostęp do tych danych za pomocą serwera proxy usługi sieci Web XML. Serwer proxy jest [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] klasą utworzoną przy użyciu jednego z nich [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Operacje usługi sieci Web XML, takie jak pobieranie klientów, umieszczanie zamówień i tak dalej, są ujawniane jako metody na serwerze proxy. Dzięki temu usługi sieci Web są znacznie łatwiejsze w użyciu niż pierwotne pliki tekstowe lub XML.  
  
 Jeśli usługa sieci Web XML działa za pośrednictwem protokołu HTTP, usługa zostanie powiązana z tymi samymi ograniczeniami zabezpieczeń co <xref:System.Net.WebClient> <xref:System.Net.HttpWebRequest> klasy i.  
  
### <a name="accessing-a-database-directly"></a>Bezpośrednie uzyskiwanie dostępu do bazy danych  
 Możesz użyć klas w <xref:System.Data> przestrzeni nazw, aby ustanowić bezpośrednie połączenia z serwerem bazy danych, takim jak SQL Server w sieci, ale musisz uwzględnić problemy z zabezpieczeniami. W przeciwieństwie do żądań HTTP, żądania połączenia bazy danych są zawsze domyślnie zabronione w obszarze częściowej relacji zaufania; takie uprawnienie będzie domyślnie stosowane tylko w przypadku instalowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji z dysku CD-ROM. Dzięki temu aplikacja jest w pełni zaufana. Aby umożliwić dostęp do określonej bazy danych SQL Server, aplikacja musi <xref:System.Data.SqlClient.SqlClientPermission> do niej zażądać; aby umożliwić dostęp do bazy danych innej niż SQL Server, musi ona zażądać <xref:System.Data.OleDb.OleDbPermission> .  
  
 W większości przypadków nie musisz uzyskiwać dostępu do bazy danych bezpośrednio, ale dostęp do niej będzie uzyskiwany przy użyciu aplikacji serwera sieci Web, która [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] została zapisywana lub usługa sieci Web XML. Dostęp do bazy danych w ten sposób jest często najlepszą metodą, jeśli [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja jest wdrażana z serwera sieci Web. Dostęp do serwera można uzyskać w częściowej relacji zaufania bez podniesienia poziomu uprawnień aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)
