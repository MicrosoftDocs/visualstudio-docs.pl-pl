---
title: Strona podpisywania, Projektant projektu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ba55795e1f1b5f54b2a863ec0163a796111d9800
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689470"
---
# <a name="signing-page-project-designer"></a>Strona podpisywania, Projektant projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj **podpisywanie** strony **projektanta projektu** do podpisywania manifestów aplikacji i wdrożenia, a także do podpisywania zestawu (podpisywanie silną nazwą).  
  
 Zauważ, że podpisywanie manifestów aplikacji i wdrożenia procesu różne od podpisywanie zestawu, mimo że oba zadania są wykonywane na **podpisywanie** strony.  
  
 Przechowywanie informacji plik klucza różni się również, podpisywania manifestu i podpisywanie zestawu. Do podpisywania manifestu klucza informacje są przechowywane w bazie danych z magazynu kryptograficznego komputera i magazynu certyfikatów Windows bieżącego użytkownika. Podpisywanie zestawu, aby uzyskać informacje o kluczu znajduje się tylko w bazie danych magazynu kryptograficznego tego komputera.  
  
 Aby uzyskać dostęp do **podpisywanie** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **podpisywanie** kartę.  
  
## <a name="application-and-deployment-manifest-signing"></a>Aplikacja i podpisywanie manifestu wdrożenia  
 **Podpisz manifesty ClickOnce** pola wyboru  
 Zaznacz to pole wyboru, aby podpisać manifesty aplikacji i wdrożenia przy użyciu pary kluczy publiczny/prywatny. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [jak: Podpisywanie aplikacji i manifestów wdrożenia](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 **Wybierz jedną z Store** przycisku  
 Umożliwia wybranie istniejącego certyfikatu z magazynu certyfikatów osobistych bieżącego użytkownika. Możesz wybrać jedną z tych certyfikatów do podpisywania manifestów Twojej aplikacji i wdrożenia.  
  
 Klikając **wybierać Store** otwiera **wybierz certyfikat** okno dialogowe, który zawiera listę certyfikatów w osobistym magazynie certyfikatów, które są aktualnie ważny (Ważny), które mają klucze prywatne. Cel certyfikatu, którą wybierzesz powinien zawierać oznaczanie kodu.  
  
 Jeśli klikniesz **wyświetlić właściwości certyfikatu**, **szczegóły certyfikatu** pojawi się okno dialogowe. To okno dialogowe zawiera szczegółowe informacje o certyfikacie i zawiera dodatkowe opcje. Możesz kliknąć pozycję **Dowiedz się więcej o certyfikatach** Aby wyświetlić dodatkowe informacje pomocy.  
  
 **Wybierz z pliku** przycisku  
 Umożliwia wybranie certyfikatu z istniejącego pliku klucza.  
  
 Klikając **wybierz z pliku** otwiera **wybierz plik** okno dialogowe, które umożliwia wybranie pliku klucza (.pfx) certyfikatu. Plik musi być chroniony hasłem i już nie może znajdować się w osobistym magazynie certyfikatów.  
  
 W **wprowadź hasło do otwarcia pliku** okna dialogowego wprowadź hasło, aby otworzyć plik klucza (.pfx) certyfikatu. Informacje hasła są przechowywane w liście osobistych kontenera kluczy i osobistym magazynie certyfikatów.  
  
 **Utwórz certyfikat testowy** przycisku  
 Służy do tworzenia certyfikatów do testowania. Certyfikat testowy służy do podpisywania manifestów aplikacji i wdrożenia ClickOnce.  
  
 Klikając **Utwórz certyfikat testu** otwiera **Utwórz certyfikat testu** okno dialogowe, w którym można wpisać hasło pliku klucza silnej nazwy dla certyfikatu testowego. Plik *projectname*_TemporaryKey.pfx. Jeśli klikniesz **OK** bez wpisywania hasła, plik PFX nie jest zaszyfrowane hasło.  
  
 **Adres URL serwera znacznika czasowego** okno  
 Określa adres serwera tej sygnatury czasowe podpisu. Po podaniu certyfikatu tej witryny zewnętrznej sprawdza czas, który został podpisany przez aplikację.  
  
## <a name="assembly-signing"></a>Podpisywanie zestawów  
 **Podpisz zestaw** pola wyboru  
 Zaznacz to pole wyboru, aby podpisać zestaw i utworzyć plik klucza o silnej nazwie. Aby uzyskać więcej informacji na temat podpisywania zestawu za pomocą **projektanta projektu**, zobacz [jak: Podpisywanie zestawu (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 Ta opcja korzysta z narzędzia Al.exe, dostarczone przez [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] do podpisywania zestawu. Aby uzyskać więcej informacji na temat Al.exe zobacz [jak: Podpisywanie zestawu silną nazwą](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 **Wybierz plik klucza o silnej nazwie** listy  
 Umożliwia określenie nowej lub istniejącej o silnej nazwie klucza pliku, który jest używany do podpisywania zestawu. Wybierz  **\<Przeglądaj … >** można wybrać istniejący plik klucza.  
  
 Wybierz  **\<nowy... >** Aby utworzyć nowy plik klucza do podpisywania zestawu. **Utwórz klucz silnej nazwy** pojawi się okno dialogowe, którym można określić nazwę pliku klucza i ochronę pliku klucza przy użyciu hasła. Hasło musi mieć co najmniej 6 znaków. Jeśli określisz hasła, zostanie utworzony plik wymiany informacji osobistych (pfx); Jeśli nie określisz hasła, zostanie utworzony plik klucza o silnej nazwie (.snk).  
  
 **Zmień hasło** przycisku  
 Zmienia hasło dla pliku klucza wymiany informacji osobistych (pfx), który jest używany do podpisywania zestawu.  
  
 Klikając **Zmień hasło** otwiera **Zmień hasło klucza** okno dialogowe. W tym oknie **stare hasło** jest bieżące hasło dla pliku klucza. **Nowe hasło** musi mieć co najmniej 6 znaków. Informacje hasła są przechowywane w magazynie certyfikatów Windows bieżącego użytkownika.  
  
 **Opóźnienie logowania tylko** pola wyboru  
 Zaznacz to pole wyboru, aby włączyć podpisywanie opóźnione.  
  
 Należy zauważyć, że opóźnienie podpisanego projektu nie będzie działać i nie można debugować. Można jednak użyć [Sn.exe (narzędzie silnych nazw)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) z `-Vr` opcję pomijania weryfikacji podczas programowania.  
  
> [!NOTE]
> Po podpisaniu zestawu nie zawsze masz dostęp do klucza prywatnego. Na przykład organizacja może być ściśle chronionej parę kluczy, deweloperzy nie mają dostępu do codziennie. Klucz publiczny mogą być dostępne, ale dostęp do klucza prywatnego jest ograniczony do kilku osób. W takim przypadku można użyć *opóźnione* lub *częściowe podpisywanie* można podać klucz publiczny, opóźnienie dodanie klucza prywatnego, dopóki nie jest przekazywane zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)   
 [Zarządzanie podpisywaniem zestawu i manifestu](../../ide/managing-assembly-and-manifest-signing.md)   
 [Silnej nazwy logowania dla zarządzanych aplikacji](https://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Instrukcje: Podpisywanie aplikacji i manifestów wdrożenia](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [Instrukcje: Podpisywanie zestawu (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Instrukcje: Podpisywanie zestawu silną nazwą](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)   
 [Zestawy o silnych nazwach](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
