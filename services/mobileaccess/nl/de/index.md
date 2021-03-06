---

copyright:
  years: 2015, 2016
lastupdated: "2016-10-02"
---


# Einführung in {{site.data.keyword.amashort}}
{: #gettingstarted}


Fügen Sie mit dem {{site.data.keyword.amafull}}-Service Sicherheit zu Ihrer mobilen App hinzu. Sie können die Clientberechtigung für den Zugriff auf geschützte Back-End-Ressourcen konfigurieren, die auf {{site.data.keyword.Bluemix_notm}} ausgeführt werden. Verwenden Sie Identitätsprovider (Google und Facebook) oder angepasste Identitäten, um Benutzer zu authentifizieren und Zugriff auf geschützte Back-End-Ressourcen und Web-Apps zu gewähren.
{:shortdesc}

**Anmerkung:** Der {{site.data.keyword.amashort}}-Service wurde früher als Advanced Mobile Access bezeichnet.


Führen Sie die folgenden Schritte aus, um den {{site.data.keyword.amashort}}-Service betriebsbereit zu machen:

1. Erstellen Sie mithilfe des {{site.data.keyword.Bluemix_notm}}-Dashboards eine mobile Back-End-Anwendung oder konfigurieren Sie eine vorhandene.
  - Sie können die **MobileFirst Services-Starter**-Boilerplate aus dem {{site.data.keyword.Bluemix_notm}}-Katalog auswählen.
  - Sie können den Service auch an eine vorhandene Anwendung binden und ihn konfigurieren.

   Wenn Sie den Starter 'MobileFirst Services' verwenden, erhalten Sie eine Instanz einer Node.js-Laufzeit, die auf IBM {{site.data.keyword.Bluemix_notm}} aktiv ist, um Ihre angepasste Back-End-Logik zu implementieren. Ein Satz von mobilen Kernservices, die Sicherheits-, Daten-, Push- und Überwachungsfunktionen bereitstellen, wird an diese Node.js-App gebunden. Nach dem Erstellen der Node.js-App in {{site.data.keyword.Bluemix_notm}} können Sie Ihre Entwicklungsumgebung einrichten und mit der Verwendung der {{site.data.keyword.Bluemix_notm}} Mobile Services-SDKs beginnen. Sie können die SDKs verwenden, um mit einfachen API-Aufrufen auf die Services zuzugreifen, die an Ihre Cloud-App gebunden sind.
  
2. Schützen Sie serverseitige Ressourcen.

   Schützen Sie Ihre mobilen Back-End-Ressourcen, die in Node.js- oder Liberty for Java&trade;-Laufzeiten aktiv sind, mit für Mobilgeräte konfigurierter OAuth-Sicherheit. Weitere Informationen finden Sie in [Ressourcen schützen](protecting-resources.html).
   Weitere Informationen zur mobilen Standard-Back-End-Anwendung finden Sie in der Beispielanwendung [bms-hellotodo-strongloop](https://github.com/ibm-bluemix-mobile-services/bms-hellotodo-strongloop).

3. Richten Sie Ihre {{site.data.keyword.amashort}}-Kernentwicklungsumgebung ein.
   
	####Cliententwicklung
   {: #client-development}
   
	Sie können das {{site.data.keyword.amashort}}-SDK folgendermaßen zu Ihrer vorhandenen Android-, iOS- oder Cordova-App hinzufügen: 
   * Android: ([Android-SDK einrichten](getting-started-android.html)) ([Beispiel](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-helloauthentication))
  
   * iOS (Swift-SDK): ([iOS-Swift-SDK einrichten](getting-started-ios-swift-sdk.html))
      ([Beispiel](https://github.com/ibm-bluemix-mobile-services/bms-samples-swift-helloauthentication))
  
   * iOS (Objective-C-SDK): ([iOS-Objective-C-SDK einrichten](getting-started-ios.html)) ([Beispiel](https://github.com/ibm-bluemix-mobile-services/bms-samples-ios-helloauthentication))

   * Cordova: ([Cordova-Plug-in einrichten](getting-started-cordova.html)) ([Beispiel](https://github.com/ibm-bluemix-mobile-services/bms-samples-cordova-helloauthentication))
   
   **Hinweis:** Das Objective-C-SDK wird zwar weiterhin vollständig unterstützt und gilt noch als primäres SDK für {{site.data.keyword.amashort}}, Verwendung und Unterstützung dieses SDK sollen jedoch zugunsten des neuen Swift-SDK noch dieses Jahr eingestellt werden. Für das Erstellen von Anwendungen wird dringend die Verwendung des Swift-SDK empfohlen (Informationen dazu siehe Abschnitt [iOS-Swift-SDK einrichten](getting-started-ios-swift-sdk.html)).

	####Webentwicklung
   {: #web-development}

   Der {{site.data.keyword.amashort}}-Service kann Ihre Webanwendung ohne spezielles SDK schützen. Zusätzlich zu dem durch den {{site.data.keyword.amashort}}-Service zur Verfügung gestellten Schutz können Sie unterschiedliche Identitätsprovider nutzen. Durch die {{site.data.keyword.amashort}}-Integration können alle Webanwendungen unabhängig von der implementierten Technologie die Vorteile des OAuth2-Protokolls nutzen. Die folgenden Abschnitte enthalten Informationen darüber, wie Sie Ihre Web-App für den Zugriff auf den {{site.data.keyword.amashort}}-Service über unterschiedliche Identitätsprovider einrichten:

    * [Facebook-Authentifizierung für Webanwendungen aktivieren](facebook-auth-web.html)
              
    * [Google-Authentifizierung für Webanwendungen aktivieren](google-auth-web.html)
              
    * [Angepasste Authentifizierung für Webanwendungen aktivieren](custom-auth-web.html)
              
4. **Optional:** Konfigurieren Sie einen Identitätsprovider für Ihre Anwendung. Pro Anwendung können Sie einen Identitätsprovider konfigurieren. Mithilfe eines konfigurierten Identitätsproviders können sich die Benutzer Ihrer mobilen App mit ihrem vorhandenen Facebook- oder Google+-Account anmelden. Alternativ können Sie eine angepasste Authentifizierung erstellen, um zu definieren, wie sich Benutzer anmelden können.
   * [Benutzer mit Facebook-Berechtigungsnachweisen authentifizieren](facebook-auth-overview.html)
   * [Benutzer mit Google-Berechtigungsnachweisen authentifizieren](google-auth-overview.html)
   * [Benutzer mit einem angepassten Identitätsprovider authentifizieren](custom-auth.html)

5. Konfigurieren Sie die Überwachung und Protokollierung der App.

    Weitere Informationen finden Sie im Abschnitt [Apps überwachen](app-monitoring.html).

# Zugehörige Links
{: #rellinks}

## Lernprogramme und Beispiele
{: #samples}
* [android-helloauthentication - Beispiel](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-helloauthentication){: new_window}
* [ios-helloauthentication - Beispiel (Swift-SDK)](https://github.com/ibm-bluemix-mobile-services/bms-samples-swift-helloauthentication){: new_window}
* [ios-helloauthentication - Beispiel (Objective-C-SDK)](https://github.com/ibm-bluemix-mobile-services/bms-samples-ios-helloauthentication){: new_window}

## SDK
{: #sdk}
* [Kern-SDK (Android)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core){: new_window}
* [Kern-SDK (Cordova-Plug-in)](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-cordova-plugin-core){: new_window}
* [Kern-SDK (iOS - Swift) ](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-core){: new_window}
* [Kern-SDK (iOS - Objective-C - nicht mehr verwendet) ](https://hub.jazz.net/git/bluemixmobilesdk/imf-ios-sdk/archive?revstr=master){: new_window}
* [Benutzerdefinierte Authentifizierung - Einfaches Beispiel](https://github.com/ibm-bluemix-mobile-services/bms-mca-custom-identity-provider-sample){: new_window}
* [Benutzerdefinierte Authentifizierung - Erweitertes Beispiel](https://github.com/ibm-bluemix-mobile-services/bms-mca-custom-identity-provider-with-user-management){: new_window}

## API-Referenz
{: api}
* [Android](https://console.{DomainName}/docs/api/content/api/mobilefirst/android/core-api-doc/overview-summary.html){: new_window}
* [iOS (Objective-C-SDK) - nicht mehr verwendet](https://console.{DomainName}/docs/api/content/api/mobilefirst/ios/IMFCore_api-doc/html/index.html){: new_window}


## Zugehörige Links
{: #general}
* [Übersicht](overview.html){: new_window}
