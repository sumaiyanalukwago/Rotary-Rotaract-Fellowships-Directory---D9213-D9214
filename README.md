# Rotary & Rotaract Club Fellowships Directory (D9213 & D9214)

Welcome to the central, open-source directory for Rotary and Rotaract Club fellowship details across **District 9213** and **District 9214**. 

This project bridges the gap for visiting Rotarians, Rotaractors, and guests trying to find fellowships across District 9213 and 9214. 

---
This project was envisioned, created, and is maintained by:
* **Sumaiya Nalukwago**
    * *President*, Rotaract Club of Mbarara City (2026/2027)
    * *Vice President of Presidents*, District 9214
    * *PR Lead*, Western Mega Fellowship (2026/2027)
    * *Club PR*, RAC Mbarara City (2026/2027)
    * *Club Administrator*, RAC Mbarara City (2025/2026)
    * *Club PR*, RAC MUST (2022/2023)
    * *Facilitator*, RYLA-D9214 (2024)
    * *Attendee*,101 DCA-D9214 (2026)

---
## 🔍 Interactive Fellowship Finder

Use the dynamic search box below to instantly filter clubs by name, district, day of the week, or meeting venue.

<!-- Raw HTML Interface Embedded into GitHub Markdown -->
<div style="background: #ffffff; padding: 20px; border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,0.05); margin-bottom: 25px; border-top: 4px solid #00246C;">
    <div style="display: flex; gap: 10px; flex-wrap: wrap; margin-bottom: 15px;">
        <input type="text" id="gitSearchInput" placeholder="🔍 Search club, town, or venue..." style="flex: 2; min-width: 200px; padding: 10px; border: 2px solid #cccccc; border-radius: 5px; font-size: 15px; outline: none;">
        <select id="gitDistrictFilter" style="flex: 1; min-width: 130px; padding: 10px; border: 2px solid #cccccc; border-radius: 5px; font-size: 15px;">
            <option value="all">All Districts</option>
            <option value="D9213">District 9213</option>
            <option value="D9214">District 9214</option>
        </select>
        <select id="gitDayFilter" style="flex: 1; min-width: 130px; padding: 10px; border: 2px solid #cccccc; border-radius: 5px; font-size: 15px;">
            <option value="all">All Days</option>
            <option value="Monday">Monday</option>
            <option value="Tuesday">Tuesday</option>
            <option value="Wednesday">Wednesday</option>
            <option value="Thursday">Thursday</option>
            <option value="Friday">Friday</option>
            <option value="Saturday">Saturday</option>
            <option value="Sunday">Sunday</option>
        </select>
    </div>
    <div id="fellowshipBadgeCounter" style="font-weight: bold; font-size: 14px; color: #555555; margin-bottom: 15px;">Showing all clubs</div>
    <div id="dynamicClubList" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 15px; max-height: 500px; overflow-y: auto; padding-right: 5px;">
        <!-- Hydrated dynamically by JavaScript -->
    </div>
</div>

<script>
(() => {
    const database = [
        // District 9213 Data Base
        { name: "Rotary Club of Kampala North", type: "Rotary", district: "D9213", day: "Monday", time: "6:00 PM", venue: "Protea Hotel, Kololo, Kampala" },
        { name: "Rotary Club of Kampala Early Bird", type: "Rotary", district: "D9213", day: "Monday", time: "7:00 AM", venue: "Hotel Africana, Kampala" },
        { name: "Rotary Club of Bukoto", type: "Rotary", district: "D9213", day: "Tuesday", time: "7:00 PM", venue: "Kabira Country Club, Kampala" },
        { name: "Rotary Club of Buwaate", type: "Rotary", district: "D9213", day: "Tuesday", time: "7:00 PM", venue: "Mukutano Meatery, Kira-Kasangati Rd" },
        { name: "Rotaract Club of Clarke International University", type: "Rotaract", district: "D9213", day: "Tuesday", time: "6:00 PM", venue: "CIU Campus, Lower Block Rm 8, Namuwongo" },
        { name: "Rotaract Club of Cape Munyonyo", type: "Rotaract", district: "D9213", day: "Tuesday", time: "6:30 PM", venue: "Ponnus Restaurant, Soya Bunga" },
        { name: "Rotary Club of Arua", type: "Rotary", district: "D9213", day: "Wednesday", time: "6:00 PM", venue: "Le Tsuba Hotel, Arua" },
        { name: "Rotaract Club of Bukoto", type: "Rotaract", district: "D9213", day: "Wednesday", time: "7:00 PM", venue: "Kabira Country Club, Kampala" },
        { name: "Rotary Club of Bugolobi", type: "Rotary", district: "D9213", day: "Wednesday", time: "6:00 PM", venue: "City Royal Hotel, Bugolobi" },
        { name: "Rotary Club of Adjumani", type: "Rotary", district: "D9213", day: "Thursday", time: "7:00 PM", venue: "Aragan Hotel, Adjumani" },
        { name: "Rotary Club of Bukedea", type: "Rotary", district: "D9213", day: "Thursday", time: "7:00 PM", venue: "Bukedea Town" },
        { name: "Rotaract Club of Cavendish University", type: "Rotaract", district: "D9213", day: "Thursday", time: "5:00 PM", venue: "Cavendish Law School, Kamwokya" },
        { name: "Rotaract Club of Bugolobi", type: "Rotaract", district: "D9213", day: "Thursday", time: "7:00 PM", venue: "City Royal Hotel, Bugolobi" },
        { name: "Rotaract Club of Buganda Royal Institute", type: "Rotaract", district: "D9213", day: "Friday", time: "6:00 PM", venue: "Buganda Royal Institute Campus" },
        { name: "Rotaract Club of Busitema University (Mbale)", type: "Rotaract", district: "D9213", day: "Friday", time: "6:00 PM", venue: "Bellodian Hall, Mbale" },
        { name: "Rotary Club of Bweyogerere Central", type: "Rotary", district: "D9213", day: "Friday", time: "7:00 PM", venue: "Unique Hotel, Bweyogerere" },
        { name: "Rotaract Club of Bugiri", type: "Rotaract", district: "D9213", day: "Sunday", time: "5:30 PM", venue: "Executive Hotel, Bugiri" },
        { name: "Rotary Club of Bulindo", type: "Rotary", district: "D9213", day: "Sunday", time: "5:00 PM", venue: "Conabry Hotel, Bulindo" },

        // District 9214 Balanced Data Base
        { name: "Rotary Club of Muyenga Bukasa", type: "Rotary", district: "D9214", day: "Monday", time: "6:30 PM", venue: "Hotel International, Muyenga" },
        { name: "Rotary Club of Moshi", type: "Rotary", district: "D9214", day: "Monday", time: "6:30 PM", venue: "Moshi Town, Tanzania" },
        { name: "Rotaract Club of Kampala City Vibrant", type: "Rotaract", district: "D9214", day: "Monday", time: "6:30 PM", venue: "Mackinnon Suites, Nakasero" },
        { name: "Rotary Club of Bunga", type: "Rotary", district: "D9214", day: "Tuesday", time: "7:00 PM", venue: "Kampala" },
        { name: "Rotary Club of Kampala Nsambya", type: "Rotary", district: "D9214", day: "Tuesday", time: "7:00 PM", venue: "Nsambya, Kampala" },
        { name: "Rotaract Club of Muyenga Tankhill", type: "Rotaract", district: "D9214", day: "Tuesday", time: "6:30 PM", venue: "Hotel International, Muyenga" },
        { name: "Rotary Club of Muyenga", type: "Rotary", district: "D9214", day: "Wednesday", time: "6:30 PM", venue: "International Hotel Muyenga, Kampala" },
        { name: "Rotary Club of Mbarara East", type: "Rotary", district: "D9214", day: "Wednesday", time: "6:00 PM", venue: "Mbarara" },
        { name: "Rotaract Club of Mbarara", type: "Rotaract", district: "D9214", day: "Wednesday", time: "6:00 PM", venue: "Adit Mall, Mbarara" },
        { name: "Rotary Club of Mbarara", type: "Rotary", district: "D9214", day: "Thursday", time: "6:00 PM", venue: "Rotary House, Mbarara" },
        { name: "Rotary Club of Muyenga Sunrise", type: "Rotary", district: "D9214", day: "Thursday", time: "7:00 AM", venue: "Hotel International, Muyenga" },
        { name: "Rotary Club of Lubowa", type: "Rotary", district: "D9214", day: "Thursday", time: "6:30 PM", venue: "Quality Shopping Village, Lubowa" },
        { name: "Rotaract Club of Mbarara City", type: "Rotaract", district: "D9214", day: "Thursday", time: "6:00 PM", venue: "Mbarara City Café" },
        { name: "Rotary Club of Kyengera Town", type: "Rotary", district: "D9214", day: "Friday", time: "7:00 PM", venue: "Kyengera, Kampala" },
        { name: "Rotary Club of Kigo Seven Lakes Golf", type: "Rotary", district: "D9214", day: "Friday", time: "6:00 PM", venue: "Lake Victoria Serena Golf Resort" },
        { name: "Rotaract Club of Kigo Seven Lakes", type: "Rotaract", district: "D9214", day: "Friday", time: "6:30 PM", venue: "Lake Victoria Serena Golf Resort" },
        { name: "Rotaract Club of Bukoba", type: "Rotaract", district: "D9214", day: "Saturday", time: "4:00 PM", venue: "Bukoba Town, Tanzania" },
        { name: "Rotaract Club of Kabale University", type: "Rotaract", district: "D9214", day: "Saturday", time: "2:00 PM", venue: "Kabale University Campus" },
        { name: "Rotary Club of Muyenga Sunday Sunset", type: "Rotary", district: "D9214", day: "Sunday", time: "5:00 PM", venue: "Hotel International, Muyenga" },
        { name: "Rotaract Club of Lukaya", type: "Rotaract", district: "D9214", day: "Sunday", time: "4:00 PM", venue: "Lukaya Town" }
    ];

    const grid = document.getElementById('dynamicClubList');
    const input = document.getElementById('gitSearchInput');
    const distFilter = document.getElementById('gitDistrictFilter');
    const dayFilter = document.getElementById('gitDayFilter');
    const counter = document.getElementById('fellowshipBadgeCounter');

    function render() {
        const term = input.value.toLowerCase();
        const dist = distFilter.value;
        const day = dayFilter.value;

        const filtered = database.filter(c => {
            const mSearch = c.name.toLowerCase().includes(term) || c.venue.toLowerCase().includes(term);
            const mDist = dist === 'all' || c.district === dist;
            const mDay = day === 'all' || c.day === day;
            return mSearch && mDist && mDay;
        });

        counter.innerText = `Found ${filtered.length} matching fellowship${filtered.length === 1 ? '' : 's'}`;
        grid.innerHTML = filtered.map(c => {
            const isRotaract = c.type.toLowerCase() === 'rotaract';
            const topColor = isRotaract ? '#D91B5C' : '#00246C';
            const badgeBg = isRotaract ? '#FCE8EF' : '#E2ECF7';
            const badgeTxt = isRotaract ? '#D91B5C' : '#00246C';
            
            return `
                <div style="background: #fdfdfd; border-radius: 6px; padding: 15px; border-top: 4px solid ${topColor}; box-shadow: 0 2px 4px rgba(0,0,0,0.05); color: #333333;">
                    <span style="display: inline-block; padding: 2px 6px; font-size: 11px; font-weight: bold; border-radius: 4px; background: ${badgeBg}; color: ${badgeTxt}; margin-bottom: 8px;">${c.type} | ${c.district}</span>
                    <h4 style="margin: 0 0 8px 0; font-size: 15px; color: #111;">${c.name}</h4>
                    <div style="font-size: 13px; margin: 4px 0;"><strong style="color: #666;">Day:</strong> ${c.day}</div>
                    <div style="font-size: 13px; margin: 4px 0;"><strong style="color: #666;">Time:</strong> ${c.time}</div>
                    <div style="font-size: 13px; margin: 4px 0;"><strong style="color: #666;">Venue:</strong> ${c.venue}</div>
                </div>
            `;
        }).join('');
    }

    input.addEventListener('input', render);
    distFilter.addEventListener('change', render);
    dayFilter.addEventListener('change', render);
    render();
})();
</script>

## Usage & Integration Instructions

Developers can integrate this directory data into custom mapping tools, mobile finders, or club websites using either a backend approach (Python) or a quick frontend build (JavaScript + CSS).
```bash
   pip install markdown beautifulsoup4
