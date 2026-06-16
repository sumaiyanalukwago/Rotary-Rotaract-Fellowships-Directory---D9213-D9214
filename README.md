# Rotary & Rotaract Club Fellowships Directory (D9213 & D9214)

Welcome to the central, open-source directory for Rotary and Rotaract Club fellowship details across **District 9213** and **District 9214**. 

This project bridges the gap for visiting Rotarians, Rotaractors, and guests trying to find fellowships across District 9213 and 9214. 

---
This project was envisioned, created, and is maintained by:
* **Sumaiya Nalukwago**
    * *President*, Rotaract Club of Mbarara City (2026/2027)
    * *Vice President of Presidents*, District 9214 (2026/2027)
    * *Attendee*,101 DCA-D9214 (2026)
    * *PR Lead*, Western Mega Fellowship (2026/2027)
    * *Club PR*, RAC Mbarara City (2026/2027)
    * *Club Administrator*, RAC Mbarara City (2025/2026)
    * *Facilitator*, RYLA-D9214 (2024)
    * *Club PR*, RAC MUST (2022/2023)
   
<!-- 📅 Weekly Fellowship Schedule Component -->
<div id="fellowshipScheduleContainer" style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; max-width: 1200px; margin: 0 auto; padding: 20px; color: #1a202c;">
    <h2 style="font-size: 24px; font-weight: 700; border-bottom: 2px solid #e2e8f0; padding-bottom: 10px; margin-bottom: 25px; color: #00246C;">
        📅 Weekly Fellowship Schedule (Sorted by Day)
    </h2>
    <div id="weeklyTimelineView">
        <!-- Injected dynamically by JavaScript -->
    </div>
</div>

<script>
(() => {
    const rawDatabase = [
        // District 9213 Database
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

        // District 9214 Database
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

    const targetDays = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
    const viewContainer = document.getElementById("weeklyTimelineView");

    let finalHTML = "";

    targetDays.forEach(currentDay => {
        // Isolate clubs running on this day iteration
        const dayClubs = rawDatabase.filter(c => c.day === currentDay);
        
        if (dayClubs.length === 0) return;

        finalHTML += `
            <div style="margin-bottom: 35px;">
                <h3 style="font-size: 18px; font-weight: 700; color: #2d3748; margin: 0 0 15px 0; display: flex; align-items: center; gap: 8px;">
                    <span style="background: #edf2f7; padding: 4px 12px; border-radius: 6px;">📌 ${currentDay}</span>
                </h3>
                <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 16px;">
        `;

        dayClubs.forEach(club => {
            const isRotaract = club.type.toLowerCase() === 'rotaract';
            const topBorderColor = isRotaract ? '#D91B5C' : '#00246C';
            const badgeBgColor = isRotaract ? '#FCE8EF' : '#E2ECF7';
            const badgeTextColor = isRotaract ? '#D91B5C' : '#00246C';

            finalHTML += `
                <div style="background: #ffffff; border: 1px solid #e2e8f0; border-top: 4px solid ${topBorderColor}; border-radius: 8px; padding: 18px; box-shadow: 0 2px 4px rgba(0,0,0,0.02); display: flex; flex-direction: column; justify-content: space-between; transition: transform 0.2s, box-shadow 0.2s;" onmouseenter="this.style.transform='translateY(-2px)'; this.style.boxShadow='0 4px 12px rgba(0,0,0,0.05)';" onmouseleave="this.style.transform='translateY(0)'; this.style.boxShadow='0 2px 4px rgba(0,0,0,0.02)';">
                    <div>
                        <span style="display: inline-block; padding: 3px 8px; font-size: 11px; font-weight: 700; border-radius: 4px; background: ${badgeBgColor}; color: ${badgeTextColor}; margin-bottom: 12px; text-transform: uppercase; letter-spacing: 0.5px;">
                            ${club.type} • ${club.district}
                        </span>
                        <h4 style="margin: 0 0 12px 0; font-size: 16px; color: #1a202c; font-weight: 700; line-height: 1.4;">
                            ${club.name}
                        </h4>
                    </div>
                    <div style="border-top: 1px dashed #e2e8f0; padding-top: 10px; font-size: 13px; color: #4a5568;">
                        <div style="margin: 4px 0; display: flex;"><span style="width: 65px; font-weight: 600; color: #718096;">Time:</span> <span style="font-weight: 500; color: #2d3748;">${club.time}</span></div>
                        <div style="margin: 4px 0; display: flex;"><span style="width: 65px; font-weight: 600; color: #718096;">Venue:</span> <span style="flex: 1; line-height: 1.3;">${club.venue}</span></div>
                    </div>
                </div>
            `;
        });

        finalHTML += `
                </div>
            </div>
        `;
    });

    viewContainer.innerHTML = finalHTML;
})();
</script>
---


