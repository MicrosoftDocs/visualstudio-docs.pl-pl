---
title: 'Instrukcje: Włącz debugowanie aplikacji ASP.NET | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 07036fd7c1db7dc8b56502ab9c914f1ba808e876
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703660"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Instrukcje: Włącz debugowanie aplikacji ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby włączyć debugowanie, należy włączyć go w obu **właściwości projektu** strony w pliku web.config aplikacji.  
  
> [!NOTE]  
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Aby włączyć debugowanie ASP.NET we właściwościach projektu (Visual Basic / C#)  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu sieci Web i wybierz **właściwości**.  
  
2. Na stronie właściwości projektu kliknij **Web** kartę.  
  
3. W obszarze **debugery**, wybierz opcję **ASP.NET** pole wyboru.  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Aby włączyć debugowanie w pliku web.config  
  
1. Otwórz plik web.config, za pomocą dowolnego edytora tekstu lub analizatora XML.  
  
    > [!NOTE]  
    > Nie masz dostępu do pliku zdalnego przy użyciu przeglądarki sieci Web, jednak. Ze względów bezpieczeństwa [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] umożliwia skonfigurowanie programu Microsoft IIS, aby zapobiec bezpośredni dostęp z przeglądarki w plikach Web.config. Jeśli próbujesz uzyskać dostęp do pliku konfiguracji, za pomocą przeglądarki, zostanie wyświetlony błąd dostępu HTTP 403 (zabronione).  
  
2. Plik Web.config jest plikiem XML, a więc zawiera zagnieżdżone sekcje oznaczone według tagów. Znajdź `configuration/system.web/compilation` elementu. Jeśli element kompilacji nie istnieje, należy go utworzyć.  
  
3. Jeśli `compilation` nie zawiera elementu `debug` atrybutu, Dodaj atrybut do elementu.  
  
4. Upewnij się, że `debug` wartość atrybutu jest równa `true`.  
  
Plik web.config powinien wyglądać podobnie jak w poniższym przykładzie. Należy pamiętać, że może być sekcje między konfiguracji i elementami system.web  
  
- Element sekcje między konfiguracji i elementami system.web  
  
- Element sekcje między elementami system.web i kompilacja  
  
- Element kompilacji może zawierać inne atrybuty i elementy  
  
## <a name="example"></a>Przykład  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] automatycznie wykrywa wszelkie zmiany w plikach Web.config i zastosowanie nowych ustawień konfiguracji. Nie trzeba ponownie uruchomić komputer lub uruchom ponownie serwer usług IIS, aby zmiany zaczęły obowiązywać.  
  
Witryna sieci Web mogą zawierać wielu wirtualnych katalogów i podkatalogów i plików Web.config mogą istnieć w każdej z nich. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacje dziedziczyć ustawienia z plików Web.config na wyższym poziomie w ścieżce adresu URL. Pliki konfiguracji hierarchiczne umożliwiają zmianę ustawień dla kilku [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, w tym samym czasie, takie jak w przypadku wszystkich aplikacji poniżej w hierarchii. Jednak jeśli `debug` jest ustawiony w pliku niżej w hierarchii, spowoduje zastąpienie wyższa wartość.  
  
Na przykład można określić `debug="true"` w www.microsoft.com/aaa/Web.config i dowolnej aplikacji w folderze aaa lub dowolnego podfolderu aaa będą dziedziczyć tego ustawienia. Więc jeśli Twoje [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacja znajduje się w www.microsoft.com/aaa/bbb, odziedziczy tego ustawienia, ponieważ żadna [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji w www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd i tak dalej. Jedynym wyjątkiem jest, jeśli jedna z tych aplikacji zastępuje ustawienie za pomocą własnego niższe pliku Web.config.  
  
Włączanie trybu debugowania będzie znacznie wpłynąć na wydajność Twojej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji. Pamiętaj, aby wyłączyć tryb debugowania, przed rozpoczęciem wdrażania aplikacji w wersji lub przeprowadzanie pomiarów wydajności.  
  
## <a name="see-also"></a>Zobacz też  
[Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
