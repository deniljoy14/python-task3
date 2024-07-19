from bs4 import BeautifulSoup
import requests, openpyxl

try:
    response = requests.get("https://www.amazon.in/minitv?ref_=nav_avod_desktop_topnav")
    response.raise_for_status() 
    soup = BeautifulSoup(response.text, 'html.parser')
    print(soup)
except Exception as e:
    print(e)
    from bs4 import BeautifulSoup
import requests, openpyxl
url = "https://www.amazon.in/minitv?ref_=nav_avod_desktop_topnav"

try:
    response = requests.get(url)
    response.raise_for_status()  
    soup = BeautifulSoup(response.text, 'html.parser')
    print("Titles:")
    titles = [element.get_text().strip() for element in soup.find_all('h3')]
    for title in titles:
        print(title)
    print("https://www.amazon.in/minitv?ref_=nav_avod_desktop_topnav")
    links = [link['href'] for link in soup.find_all('a', href=True)]
    for link in links:
        print(link)
    print("\nImages:")
    images = [img['src'] for img in soup.find_all('img', src=True)]
    for img in images:
        print(img)
    workbook = openpyxl.Workbook()
    sheet = workbook.active
    sheet.title = "IMDB Fan Favorites"
    for index, title in enumerate(titles, start=1):
        sheet[f'A{index}'] = title
    for index, link in enumerate(links, start=1):
        sheet[f'B{index}'] = link

    for index, img in enumerate(images, start=1):
        sheet[f'C{index}'] = img
    workbook.save("amazon_Fan_Favorites.xlsx")
    print("\nData saved to amazon_Fan_Favorites.xlsx")

except Exception as e:
    print(e)
