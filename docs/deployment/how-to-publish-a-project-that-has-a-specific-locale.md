---
title: 'Instrukcje: Publikowanie projektu o specyficznych ustawieniach regionalnych | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70300e7d6090e7c8155281e771522bec08308f5b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629667"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Instrukcje: Publikowanie projektu o specyficznych ustawieniach regionalnych
Nie jest niczym niezwykłym aplikacji zawierają składniki, które mają różnych ustawień regionalnych. W tym scenariuszu może utworzyć rozwiązanie, które ma kilka projektów, a następnie opublikuj oddzielnych projektów dla poszczególnych ustawień regionalnych. Ta procedura pokazuje, jak publikować pierwszego projektu w rozwiązaniu przy użyciu ustawień regionalnych "PL" za pomocą makra. Jeśli chcesz wypróbować tę procedurę za pomocą ustawień regionalnych innych niż "en", upewnij się ustawić `localeString` w makrze zgodne z ustawieniami regionalnymi, którego używasz (na przykład, "de" lub "de-DE").

> [!NOTE]
>  Użycie tego makra, Opublikuj Lokalizacja powinna być udział prawidłowy adres URL lub Universal Naming Convention (UNC). Ponadto usługi Internet Information Services (IIS) musi być zainstalowany na tym komputerze. Aby zainstalować usługi IIS, na **Start** menu, kliknij przycisk **Panelu sterowania**. Kliknij dwukrotnie **Dodaj lub usuń programy**. W **apletu Dodaj lub usuń programy**, kliknij przycisk **Dodaj/Usuń składniki Windows**. W **Kreatora składników Windows**, wybierz opcję **Internet Information Services (IIS)** pole wyboru w **składniki** listy. Następnie kliknij przycisk **Zakończ** aby zamknąć kreatora.

### <a name="to-create-the-publishing-macro"></a>Aby utworzyć publikowania — makro

1.  Aby otworzyć Eksplorator makr w **narzędzia** menu wskaż **makra**, a następnie kliknij przycisk **Eksplorator makr**.

2.  Utwórz nowy moduł makra. W Eksploratorze — makro wybierz **MyMacros**. Na **narzędzia** menu wskaż **makra**, a następnie kliknij przycisk **nowy moduł — makro**. Nazwa modułu **PublishSpecificCulture**.

3.  W Eksploratorze — makro rozwiń **MyMacros** węzeł, a następnie otwórz **PublishAllProjects** modułu, klikając go dwukrotnie (lub z **narzędzia** wskaż **Makra**, a następnie kliknij przycisk **makrach IDE**).

4.  W makrach IDE, Dodaj następujący kod do modułu, po `Import` instrukcji:

    ```vb
    Module PublishSpecificCulture
        Sub PublishProjectFirstProjectWithEnLocale()
            ' Note: You should publish projects by using the IDE at least once
            ' before you use this macro. Items such as the certificate and the
            ' security zone must be set.
            Dim localeString As String = "en"

            ' Get first project.
            Dim proj As Project = DTE.Solution.Projects.Item(1)
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value

            ' GenerateManifests and SignManifests must always be set to
            ' True for publishing to work.
            proj.Properties.Item("GenerateManifests").Value = True
            proj.Properties.Item("SignManifests").Value = True

            'Set the publish language.
            'This will set the deployment language and pick up all
            ' en resource dlls:
            Dim originalTargetCulture As String = _
                publishProperties.Item("TargetCulture").Value
            publishProperties.Item("TargetCulture").Value = localeString

            'Append 'en' to end of publish, install, and update URLs if needed:
            Dim originalPublishUrl As String = _
                publishProperties.Item("PublishUrl").Value
            Dim originalInstallUrl As String = _
                publishProperties.Item("InstallUrl").Value
            Dim originalUpdateUrl As String = _
                publishProperties.Item("UpdateUrl").Value
            publishProperties.Item("PublishUrl").Value = _
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))
            If originalInstallUrl <> String.Empty Then
                publishProperties.Item("InstallUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))
            End If
            If originalUpdateUrl <> String.Empty Then
                publishProperties.Item("UpdateUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))
            End If
            proj.Save()

            Dim slnbld2 As SolutionBuild2 = _
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)
            slnbld2.Clean(True)

            slnbld2.BuildProject( _
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
            proj.UniqueName, True)

            ' Only publish if build is successful.
            If slnbld2.LastBuildInfo <> 0 Then
                MsgBox("Build failed for " & proj.UniqueName)
            Else
                slnbld2.PublishProject( _
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
                proj.UniqueName, True)
                If slnbld2.LastPublishInfo = 0 Then
                    MsgBox("Publish succeeded for " & proj.UniqueName _
                    & vbCrLf & "." _
                    & " Publish Language was '" & localeString & "'.")
                Else
                    MsgBox("Publish failed for " & proj.UniqueName)
                End If
            End If

            ' Return URLs and target culture to their previous state.
            publishProperties.Item("PublishUrl").Value = originalPublishUrl
            publishProperties.Item("InstallUrl").Value = originalInstallUrl
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl
            publishProperties.Item("TargetCulture").Value = originalTargetCulture
            proj.Save()
        End Sub

        Private Function AppendStringToUrl(ByVal str As String, _
        ByVal baseUri As Uri) As String
            Dim returnValue As String = baseUri.OriginalString
            If baseUri.IsFile OrElse baseUri.IsUnc Then
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)
            Else
                If Not baseUri.ToString.EndsWith("/") Then
                    returnValue = baseUri.OriginalString & "/" & str
                Else
                    returnValue = baseUri.OriginalString & str
                End If
            End If
            Return returnValue
        End Function
    End Module
    ```

5.  Zamknij makra środowiska IDE. Fokus powrót do programu Visual Studio.

### <a name="to-publish-a-project-for-a-specific-locale"></a>Publikowanie projektu o specyficznych ustawieniach regionalnych

1.  Aby utworzyć projekt aplikacji Windows Visual Basic w **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.

2.  W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji Windows** z **języka Visual Basic** węzła. Nadaj projektowi nazwę *PublishLocales*.

3.  Kliknij z formularza Form1. W **właściwości** okna, w obszarze **projektowania**, zmień **języka** właściwość **(opcja domyślna)** do **wjęzykuangielskim**. Zmiana **tekstu** właściwości formularza w celu **MyForm**.

     Należy pamiętać, że zlokalizowany zasób biblioteki DLL nie są tworzone, dopóki nie są potrzebne. Na przykład są one tworzone po zmianie tekstu w formularzu lub jego formantów po określeniu nowych ustawień regionalnych.

4.  Publikowanie *PublishLocales* przy użyciu programu Visual Studio IDE.

     W **Eksploratora rozwiązań**, wybierz opcję *PublishLocales*. Na **projektu** menu, wybierz opcję **właściwości**. W Projektancie projektu na **Publikuj** Określ lokalizację publikacji, **http://localhost/PublishLocales**, a następnie kliknij przycisk **Publikuj teraz**.

     Po wyświetleniu strony sieci Web publikowania należy go zamknąć. (W tym kroku należy opublikować projekt, nie trzeba go zainstalować.)

5.  Publikowanie *PublishLocales* ponownie przez wywołanie makra w oknie wiersza polecenia programu Visual Studio. Aby wyświetlić okno wiersza polecenia na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **okna polecenia**, lub naciśnij **Ctrl** + **Alt**+**A**. W oknie wiersza polecenia, wpisz `macros`; Autouzupełnianie udostępni listy dostępnych makr. Wybierz Poniższe makro, a następnie naciśnij klawisz ENTER:

     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`

6.  Gdy proces publikowania zakończy się powodzeniem, zostanie wygenerowany komunikat z informacją "Publikowanie zakończyło się pomyślnie *PublishLocales\PublishLocales.vbproj*. Publikowanie język został "en". " Kliknij przycisk **OK** w oknie komunikatu. Po wyświetleniu strony sieci Web publikowania kliknij **zainstalować**.

7.  Szukaj w *C:\Inetpub\wwwroot\PublishLocales\en*. Powinien zostać wyświetlony zainstalowanych plików, takich jak manifestów *setup.exe*i publikowania pliku strony sieci Web, oprócz zlokalizowany plik DLL zasobów. (Domyślnie funkcja ClickOnce dołącza *.deploy* rozszerzenia dla plików exe i dll; Usuń to rozszerzenie, po wdrożeniu.)

## <a name="see-also"></a>Zobacz także
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Makra środowiska deweloperskiego](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))
- [Okno Eksploratora — makro](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))
- [Instrukcje: Edytowanie i programowe tworzenie makra](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))