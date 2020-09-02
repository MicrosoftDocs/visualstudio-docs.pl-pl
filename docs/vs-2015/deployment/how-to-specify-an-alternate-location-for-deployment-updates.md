---
title: 'Instrukcje: Określanie alternatywnej lokalizacji aktualizacji wdrożenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037223"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Porady: określanie alternatywnej lokalizacji aktualizacji wdrażania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz zainstalować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację początkowo z dysku CD lub udziału plików, ale aplikacja musi sprawdzić, czy aktualizacje są okresowo aktualizowane w sieci Web. Możesz określić alternatywną lokalizację aktualizacji w manifeście wdrożenia, aby aplikacja mogła ją zaktualizować do sieci Web po jej początkowej instalacji.  
  
> [!NOTE]
> Aby można było korzystać z tej funkcji, aplikacja musi być skonfigurowana do instalacji lokalnie. Aby uzyskać więcej informacji, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ponadto, jeśli zainstalujesz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację z sieci, ustawienie alternatywnej lokalizacji spowoduje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] użycie tej lokalizacji zarówno w przypadku instalacji początkowej, jak i wszystkich kolejnych aktualizacji. Jeśli aplikacja jest instalowana lokalnie (na przykład z dysku CD), początkowa instalacja jest przeprowadzana przy użyciu oryginalnego nośnika, a wszystkie kolejne aktualizacje będą korzystały z lokalizacji alternatywnej.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Określanie alternatywnej lokalizacji aktualizacji za pomocą MageUI.exe (Narzędzie oparte na Windows Forms)  
  
1. Otwórz .NET Framework wiersz polecenia i wpisz:  
  
     **mageui.exe**  
  
2. W menu **plik** wybierz polecenie **Otwórz** , aby otworzyć manifest wdrożenia aplikacji.  
  
3. Wybierz kartę **Opcje wdrażania** .  
  
4. W polu tekstowym o nazwie **Lokalizacja uruchamiania**wprowadź adres URL katalogu, który będzie zawierać manifest wdrożenia dla aktualizacji aplikacji.  
  
5. Zapisz manifest wdrożenia.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Określanie alternatywnej lokalizacji aktualizacji za pomocą Mage.exe  
  
1. Otwórz wiersz polecenia .NET Framework.  
  
2. Ustaw lokalizację aktualizacji przy użyciu następującego polecenia. W tym przykładzie **HelloWorld.exe. Application** to ścieżka do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikacji, która zawsze ma rozszerzenie. Application i `http://adatum.com/Update/Path` jest adresem URL, który [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] będzie sprawdzać dostępność aktualizacji aplikacji.  
  
     **Mage — aktualizacja HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/Update/Path**  
  
3. Zapisz plik.  
  
    > [!NOTE]
    > Teraz musisz ponownie podpisać plik za pomocą Mage.exe. Aby uzyskać więcej informacji, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 W przypadku instalowania aplikacji z nośnika w trybie offline, takiego jak dysk CD, a komputer jest w trybie online, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] należy najpierw sprawdzić adres URL określony przez `<deploymentProvider>` tag w manifeście wdrożenia, aby określić, czy lokalizacja aktualizacji zawiera nowszą wersję aplikacji. Jeśli tak, program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zainstaluje aplikację bezpośrednio z tego miejsca, zamiast z katalogu instalacji początkowej, a środowisko uruchomieniowe języka wspólnego (CLR) określi poziom zaufania aplikacji przy użyciu `<deploymentProvider>` . Jeśli komputer jest w trybie offline lub `<deploymentProvider>` jest nieosiągalny, program jest [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalowany z dysku CD, a środowisko CLR przyznaje zaufanie na podstawie punktu instalacji; w przypadku instalacji z dysku CD oznacza to, że aplikacja otrzymuje pełne zaufanie. Wszystkie kolejne aktualizacje będą dziedziczyć ten poziom zaufania.  
  
 Wszystkie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje, które używają, `<deploymentProvider>` powinny jawnie zadeklarować wymagane uprawnienia w manifeście aplikacji, tak aby aplikacja nie otrzymywała różnych poziomów zaufania na różnych komputerach.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
