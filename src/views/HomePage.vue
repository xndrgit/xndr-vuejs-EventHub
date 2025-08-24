<template>
  <div class="home-page">
    <main class="main-content">
      <div v-if="loading" class="loading">Loading events...</div>
      <div v-else-if="events.length === 0" class="no-events">
        No upcoming events are available at this time.
      </div>
      <div v-else class="events-grid">
        <div v-for="event in filteredEvents" :key="event.id" class="event-card">
          <img :src="event.imageUrl" :alt="event.title + ' Image'" class="event-image" />
          <div class="event-details">
            <h3>{{ event.title }}</h3>
            <p><strong>Date:</strong> {{ formatDate(event.date) }}</p>
            <p><strong>Registration Deadline:</strong> {{ formatDate(event.regDeadline) }}</p>
            <p>
              <strong>Spots Available:</strong> {{ event.availableSpots }} / {{ event.maxSpots }}
            </p>
            <button class="book-button" @click="bookEvent(event.id)">Book Now</button>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  components: {
  },
  data() {
    return {
      events: [],
      loading: true,
      currentDate: new Date('2025-08-25'),
    }
  },
  computed: {
    filteredEvents() {
      return this.events.filter((event) => {
        const eventDate = new Date(event.date)
        return eventDate >= this.currentDate
      })
    },
  },
  created() {
    setTimeout(() => {
      this.events = [
        {
          id: 1,
          title: 'Golf',
          date: '2025-09-15',
          regDeadline: '2025-09-10',
          availableSpots: 5,
          maxSpots: 20,
          imageUrl: '/assets/golf.jpg',
        },
        {
          id: 2,
          title: 'Training',
          date: '2025-10-05',
          regDeadline: '2025-09-30',
          availableSpots: 10,
          maxSpots: 15,
          imageUrl: '/assets/training.jpg',
        },
        {
          id: 3,
          title: 'Tour',
          date: '2025-11-20',
          regDeadline: '2025-11-15',
          availableSpots: 8,
          maxSpots: 12,
          imageUrl: '/assets/tour.jpg',
        },
      ]
      this.loading = false
    }, 1000)
  },
  methods: {
    bookEvent(id) {
      alert(`Booking event with ID: ${id}`)
    },
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString('en-US', { year: 'numeric', month: 'long', day: 'numeric' })
    },
  },
}
</script>

<style scoped lang="scss">
.home-page {
  color: #1d1d1f;
  background-color: #f5f5f7;
  min-height: 80vh;
  display: flex;
  flex-direction: column;
}

.main-content {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 32px 16px;
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.loading,
.no-events {
  text-align: center;
  font-size: 1rem;
  color: #6e6e73;
  padding: 24px;
  background-color: #ffffff;
  border: 1px solid #d2d2d7;
  max-width: 600px;
  width: 100%;
}

.events-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
  width: 100%;
}

.event-card {
  background-color: #ffffff;
  border: 1px solid #d2d2d7;
  display: flex;
  flex-direction: column;
}

.event-image {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-bottom: 1px solid #d2d2d7;
}

.event-details {
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.event-card h3 {
  font-size: 1.25rem;
  font-weight: 600;
  margin: 0;
}

.event-card p {
  font-size: 0.875rem;
  margin: 0;
  color: #6e6e73;
}

.event-card p strong {
  color: #1d1d1f;
}

.book-button {
  margin-top: auto;
  width: 100%;
  background-color: #0071e3;
  color: #ffffff;
  border: none;
  padding: 12px;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
}

@media (max-width: 768px) {
  .main-content {
    padding: 24px 12px;
  }

  .event-image {
    height: 140px;
  }

  .event-details {
    padding: 16px;
    gap: 6px;
  }

  .event-card h3 {
    font-size: 1.125rem;
  }

  .event-card p {
    font-size: 0.8125rem;
  }

  .book-button {
    padding: 10px;
    font-size: 0.875rem;
  }
}
</style>
