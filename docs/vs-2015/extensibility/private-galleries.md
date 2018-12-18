---
title: Galerie prywatne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 910764df2f6a6e3069136bce64b77f267e473b9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749956"
---
# <a name="private-galleries"></a>Galerie prywatne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz udostępnić formanty, szablony i narzędzia, które tworzysz, publikując je do *prywatną galerię* w sieci intranet dla całej organizacji, w następujący sposób:  
  
-   Utwórz Atom () kanału informacyjnego RSS do odpowiednio skonfigurowanego centralną lokalizację (repozytorium) w sieci intranet. Aby uzyskać więcej informacji, zobacz [jak: utworzyć źródło danych Atom dla galerii prywatnej](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Dystrybuuj plik .pkgdef, który opisuje prywatną galerię. Firma Microsoft zaleca tej konfiguracji dla administratorów, którzy chcą nawiązać ona prywatną galerię na wielu komputerach jednocześnie.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Dodawanie galerii prywatnej do rozszerzenia i aktualizacje w programie Visual Studio  
 Po udostępnieniu ona prywatną galerię można dodać go do **rozszerzenia i aktualizacje** w programie Visual Studio.  
  
 ![Okno dialogowe dodawania Menedżera rozszerzenia](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Aby dodać ona prywatną galerię do rozszerzenia i aktualizacje  
  
1.  Na pasku menu wybierz **narzędzia**, **opcje**.  
  
2.  W **środowiska** węzeł **rozszerzenia i aktualizacje**.  
  
3.  Wybierz **Dodaj** przycisku.  
  
4.  W **nazwa** na przykład wprowadź nazwę dla galerii prywatnej `My Gallery`.  
  
5.  W **adresu URL** wprowadź adres URL strumieniowego źródła Atom lub witryny programu SharePoint, który jest hostem prywatną galerię.  
  
    1.  Jeśli host znajduje się źródło danych Atom łączący się z prywatną galerię, adres URL będzie przypominać ten: http://www.mywebsite/mygallery/atom.xml.  Ten adres URL może odwoływać się do pliku lub ścieżkę sieciową.  
  
    2.  Jeśli host jest witryną programu SharePoint, adres URL będzie podobny do tego: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Zarządzanie galerie prywatne  
 Administrator może udostępnić ona prywatną galerię na kilku komputerach jednocześnie przez modyfikację rejestru systemu na każdym komputerze. W tym celu należy utworzyć plik .pkgdef, który zawiera opis nowych kluczy rejestru i ich wartości.  Format ten plik jest w następujący sposób.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie prywatnej Galerii za pomocą ustawień rejestru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalowanie rozszerzenia z galerii prywatnej  
 Można wyszukać i zainstalować rozszerzenia programu Visual Studio z prywatną galerię w **rozszerzenia i aktualizacje**. Użyto ona prywatną galerię o nazwie `My Gallery`.  
  
 ![Menedżer rozszerzeń instalowanie galerią prywatną](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Aby wyszukać i zainstalować rozszerzenia z galerii prywatnej  
  
1.  Na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
2.  W okienku po lewej stronie wybierz **rozszerzeń Online**, a następnie wybierz pozycję **Moja Galeria**.  
  
3.  W okienku po prawej stronie zaznacz rozszerzenie, a następnie wybierz **Pobierz** przycisku.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Trwa aktualizowanie rozszerzenia z galerii prywatnej  
 Jak nowe wersje rozszerzeń programu Visual Studio są ogłaszane w galerii prywatnej, należy zaktualizować rozszerzenia, które zostały zainstalowane. Użyto ona prywatną galerię o nazwie `My Repository`.  
  
 ![Aktualizacja galerii prywatnej Menedżer rozszerzenia](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Aby zaktualizować zainstalowanego rozszerzenia z galerii prywatnej  
  
1.  Na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
2.  W okienku po lewej stronie wybierz **aktualizacje**, a następnie wybierz pozycję **Moje repozytorium**.  
  
3.  W okienku po prawej stronie zaznacz rozszerzenie, a następnie wybierz **aktualizacji** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie rozszerzeń programu Visual Studio i korzystanie](../ide/finding-and-using-visual-studio-extensions.md)   
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

